---
title: Omówienie narzędzia WCF svcutil
description: Omówienie narzędzia Microsoft WCF dotnet-svcutil, które dodaje funkcje dla projektów .NET Core i ASP.NET Core, podobne do narzędzia WCF svcutil dla projektów .NET Framework.
author: mlacouture
ms.date: 02/22/2019
ms.openlocfilehash: 0607c73935f319f2cc0d8d9f92d96a4c71c54edf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920945"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a>Narzędzie WCF dotnet-svcutil dla .NET Core

Narzędzie **Dotnet-svcutil** w programie Windows Communication Foundation (WCF) jest narzędziem .NET, które pobiera metadane z usługi sieci web w lokalizacji sieciowej lub z pliku WSDL i generuje klasę WCF zawierającą metody proxy klienta, które uzyskują dostęp do operacji usługi sieci web.

Podobnie jak w [**przypadku metadanych modelu usługi — svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) dla projektów .NET Framework, **dotnet-svcutil** jest narzędziem wiersza polecenia do generowania odwołania do usługi sieci web zgodnego z projektami .NET Core i .NET Standard.

Narzędzie **dotnet-svcutil** jest alternatywną opcją dla dostawcy usług [**sieci Web WCF Visual**](wcf-web-service-reference-guide.md) Studio, który po raz pierwszy został dostarczony z programiem Visual Studio 2017 w wersji 15.5. Narzędzie **dotnet-svcutil** jako narzędzie .NET jest dostępne na wielu platformach w systemach Linux, macOS i Windows.

> [!IMPORTANT]
> Należy odwoływać się tylko do usług z zaufanego źródła. Dodawanie odwołań z niezaufanego źródła może naruszyć bezpieczeństwo.

## <a name="prerequisites"></a>Wymagania wstępne

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

- [.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) lub nowsze wersje
- Twój ulubiony edytor kodu

# <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

- [.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) lub nowsze wersje
- Twój ulubiony edytor kodu

---

## <a name="getting-started"></a>Wprowadzenie

W poniższym przykładzie przedstawiono kroki wymagane do dodania odwołania do usługi sieci web do projektu sieci web .NET Core i wywołania usługi. Utworzysz aplikację sieci web .NET Core o nazwie *HelloSvcutil* i dodasz odwołanie do usługi sieci web, która implementuje następujący kontrakt:

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

W tym przykładzie załóżmy, że usługa sieci web będzie hostowana pod następującym adresem:`http://contoso.com/SayHello.svc`

W oknie polecenia systemu Windows, macOS lub Linux wykonaj następujące czynności:

1. Utwórz katalog o nazwie _HelloSvcutil_ dla swojego projektu i uczyń go bieżącym katalogiem, jak w poniższym przykładzie:

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. Utwórz nowy projekt sieci Web języka [`dotnet new`](../tools/dotnet-new.md) C# w tym katalogu, używając następującego polecenia:

    ```dotnetcli
    dotnet new web
    ```

3. Zainstaluj [ `dotnet-svcutil` pakiet NuGet](https://nuget.org/packages/dotnet-svcutil) jako narzędzie cli: <!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)
    Otwórz `HelloSvcutil.csproj` plik projektu w edytorze, `Project` edytować element i dodać [ `dotnet-svcutil` pakiet NuGet](https://nuget.org/packages/dotnet-svcutil) jako odwołanie do narzędzia CLI, używając następującego kodu:

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    Następnie przywróć pakiet _dotnet-svcutil_ za pomocą następującego [`dotnet restore`](../tools/dotnet-restore.md) polecenia:

    ```dotnetcli
    dotnet restore
    ```

    ---

4. Uruchom polecenie _dotnet-svcutil,_ aby wygenerować plik referencyjny usługi sieci web w następujący sposób:

    # <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

    ```dotnetcli
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

Wygenerowany plik jest zapisywany jako _HelloSvcutil/ServiceReference/Reference.cs_. Narzędzie _dotnet-svcutil_ dodaje również do projektu odpowiednie pakiety WCF wymagane przez kod proxy jako odwołania do pakietu.

## <a name="using-the-service-reference"></a>Korzystanie z dokumentacji serwisowej

1. Przywróć pakiety WCF [`dotnet restore`](../tools/dotnet-restore.md) za pomocą polecenia w następujący sposób:

    ```dotnetcli
    dotnet restore
    ```

2. Znajdź nazwę klasy klienta i operacji, której chcesz użyć. `Reference.cs`będzie zawierać klasę, która `System.ServiceModel.ClientBase`dziedziczy z , z metodami, które mogą służyć do wywoływania operacji w usłudze. W tym przykładzie chcesz wywołać _usługę_ _SayHello_ Hello operacji. `ServiceReference.SayHelloClient`jest nazwą klasy klienta i ma metodę `HelloAsync` o nazwie, która może służyć do wywołania operacji.

3. Otwórz `Startup.cs` plik w edytorze i dodaj using instrukcji dla obszaru nazw odwołania do usługi u góry:

    ```csharp
    using ServiceReference;
    ```

4. Edytowanie `Configure` metody wywoływania usługi sieci web. Można to zrobić, tworząc wystąpienie klasy, `ClientBase` która dziedziczy z i wywołanie metody na obiekcie klienta:

    ```csharp
    public void Configure(IApplicationBuilder app, IHostingEnvironment env)
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

5. Uruchom aplikację przy [`dotnet run`](../tools/dotnet-run.md) użyciu polecenia w następujący sposób:

    ```dotnetcli
    dotnet run
    ```

6. Przejdź do adresu URL wymienionego w `http://localhost:5000`konsoli (na przykład) w przeglądarce internetowej.

Powinieneś zobaczyć następujące dane wyjściowe: "Hello dotnet-svcutil!"

Aby uzyskać szczegółowy `dotnet-svcutil` opis parametrów narzędzia, wywołaj narzędzie przekazujące parametr pomocy w następujący sposób:
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

Jeśli masz jakiekolwiek pytania lub opinie, [otwórz problem w usiuercie GitHub](https://github.com/dotnet/wcf/issues/new). Możesz również przejrzeć wszystkie istniejące pytania lub problemy [w reppo WCF w githubie](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

## <a name="release-notes"></a>Informacje o wersji

- Informacje o [wydaniu można znaleźć](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) w informacjach o wydaniu, w tym znanych problemach.

## <a name="information"></a>Informacje

- [pakiet NuGet dotnet-svcutil](https://nuget.org/packages/dotnet-svcutil)
