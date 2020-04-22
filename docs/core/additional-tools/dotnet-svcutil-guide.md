---
title: Przegląd narzędzi WCF svcutil
description: Omówienie narzędzia Microsoft WCF dotnet-svcutil, które dodaje funkcje dla projektów .NET Core i ASP.NET Core, podobne do narzędzia Svcutil WCF dla projektów .NET Framework.
author: mlacouture
ms.date: 02/22/2019
ms.openlocfilehash: 1f500c9355112183a135c2b639807c7cd62fbbfc
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021253"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a>Narzędzie WCF dotnet-svcutil dla .NET Core

Narzędzie **dotnet-svcutil** programu Windows Communication Foundation (WCF) to narzędzie .NET, które pobiera metadane z usługi sieci web w lokalizacji sieciowej lub z pliku WSDL i generuje klasę WCF zawierającą metody proxy klienta, które uzyskują dostęp do operacji usługi sieci web.

Podobnie jak w przypadku [**narzędzia Metadane modelu usługi — svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) dla projektów .NET Framework, **dotnet-svcutil** jest narzędziem wiersza polecenia do generowania odwołania do usługi sieci web zgodnej z projektami .NET Core i .NET Standard.

Narzędzie **dotnet-svcutil** jest alternatywną opcją dla dostawcy usług połączonych w programie [**Visual Studio,**](wcf-web-service-reference-guide.md) który po raz pierwszy został dostarczony z programem Visual Studio 2017 w wersji 15.5. Narzędzie **dotnet-svcutil** jako narzędzie .NET jest dostępne na wielu platformach w systemach Linux, macOS i Windows.

> [!IMPORTANT]
> Należy odwoływać się tylko do usług z zaufanego źródła. Dodawanie odwołań z niezaufanego źródła może naruszyć bezpieczeństwo.

## <a name="prerequisites"></a>Wymagania wstępne

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

- [Plik SDK programu .NET Core 2.1](https://dotnet.microsoft.com/download) lub nowszych
- Twój ulubiony edytor kodu

# <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

- [Plik SDK programu .NET Core 1.0.4](https://dotnet.microsoft.com/download) lub nowszych
- Twój ulubiony edytor kodu

---

## <a name="getting-started"></a>Wprowadzenie

W poniższym przykładzie przedstawiono kroki wymagane do dodania odwołania do usługi sieci web do projektu sieci web .NET Core i wywołania usługi. Utworzysz aplikację sieci web .NET Core o nazwie *HelloSvcutil* i dodasz odwołanie do usługi sieci web, która implementuje następującą umowę:

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

W tym przykładzie załóżmy, że usługa sieci web będzie hostowana pod następującym adresem:`http://contoso.com/SayHello.svc`

Z okna polecenia systemu Windows, macOS lub Linux wykonaj następujące czynności:

1. Utwórz katalog o nazwie _HelloSvcutil_ dla projektu i uczynić go bieżącym katalogiem, jak w poniższym przykładzie:

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. Utwórz nowy projekt sieci Web języka [`dotnet new`](../tools/dotnet-new.md) C# w tym katalogu za pomocą polecenia w następujący sposób:

    ```dotnetcli
    dotnet new web
    ```

3. Zainstaluj [ `dotnet-svcutil` pakiet NuGet](https://nuget.org/packages/dotnet-svcutil) jako narzędzie interfejsu wiersza polecenia: <!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)
    Otwórz `HelloSvcutil.csproj` plik projektu w edytorze, edytuj `Project` element i dodaj pakiet [ `dotnet-svcutil` NuGet](https://nuget.org/packages/dotnet-svcutil) jako odwołanie do narzędzia interfejsu wiersza polecenia, używając następującego kodu:

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    Następnie przywróć pakiet _dotnet-svcutil_ za pomocą polecenia w [`dotnet restore`](../tools/dotnet-restore.md) następujący sposób:

    ```dotnetcli
    dotnet restore
    ```

    ---

4. Uruchom polecenie _dotnet-svcutil,_ aby wygenerować plik odwołania do usługi sieci web w następujący sposób:

    # <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

    ```dotnetcli
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

Wygenerowany plik jest zapisywany jako _HelloSvcutil/ServiceReference/Reference.cs_. Narzędzie _dotnet-svcutil_ dodaje również do projektu odpowiednie pakiety WCF wymagane przez kod serwera proxy jako odwołania do pakietu.

## <a name="using-the-service-reference"></a>Korzystanie z odwołania do usługi

1. Przywróć pakiety [`dotnet restore`](../tools/dotnet-restore.md) WCF za pomocą polecenia w następujący sposób:

    ```dotnetcli
    dotnet restore
    ```

2. Znajdź nazwę klasy klienta i operacji, której chcesz użyć. `Reference.cs`będzie zawierać klasę, która `System.ServiceModel.ClientBase`dziedziczy z , z metod, które mogą służyć do wywoływania operacji w usłudze. W tym przykładzie chcesz wywołać operację _Hello_ usługi _SayHello._ `ServiceReference.SayHelloClient`jest nazwą klasy klienta i ma metodę `HelloAsync` o nazwie, która może służyć do wywołania operacji.

3. Otwórz `Startup.cs` plik w edytorze i dodaj instrukcję using dla obszaru nazw odwołania do usługi u góry:

    ```csharp
    using ServiceReference;
    ```

4. Edytuj `Configure` metodę wywoływania usługi sieci web. Można to zrobić, tworząc wystąpienie klasy, `ClientBase` która dziedziczy i wywołując metodę w obiekcie klienta:

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }

        app.Run(async (context) =>
        {
            var client = new SayHelloClient();
            var response = await client.HelloAsync();
            await context.Response.WriteAsync(response);
        });
    }

    ```

5. Uruchom aplikację za [`dotnet run`](../tools/dotnet-run.md) pomocą polecenia w następujący sposób:

    ```dotnetcli
    dotnet run
    ```

6. Przejdź do adresu URL wymienionego w `http://localhost:5000`konsoli (na przykład) w przeglądarce internetowej.

Powinieneś zobaczyć następujące dane wyjściowe: "Hello dotnet-svcutil!"

Aby uzyskać szczegółowy `dotnet-svcutil` opis parametrów narzędzia, wywołać narzędzie przekazując parametr pomocy w następujący sposób:
# <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

```dotnetcli
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

```dotnetcli
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a>Opinie & pytania

Jeśli masz jakieś pytania lub opinie, [otwórz problem w usłudze GitHub](https://github.com/dotnet/wcf/issues/new). Możesz również przejrzeć wszelkie istniejące pytania lub problemy [w repozytorium WCF na GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

## <a name="release-notes"></a>Informacje o wersji

- Informacje o wersji można znaleźć w [informacjach o](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) wersji, w tym o znanych problemach.

## <a name="information"></a>Informacje

- [Pakiet dotnet-svcutil NuGet](https://nuget.org/packages/dotnet-svcutil)
