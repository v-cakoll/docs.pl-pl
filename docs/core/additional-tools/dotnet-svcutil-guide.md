---
title: Omówienie narzędzia WCF Svcutil
description: Omówienie narzędzia dotnet-Svcutil programu Microsoft WCF, które dodaje funkcje dla projektów .NET Core i ASP.NET Core, podobnie jak narzędzie WCF Svcutil dla projektów .NET Framework.
author: mlacouture
ms.date: 02/22/2019
ms.openlocfilehash: 0607c73935f319f2cc0d8d9f92d96a4c71c54edf
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920945"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a>WCF dotnet-Svcutil Tool dla platformy .NET Core

Windows Communication Foundation (WCF) **dotnet-Svcutil** jest narzędziem platformy .NET, które pobiera metadane z usługi sieci Web w lokalizacji sieciowej lub z pliku WSDL, i GENERUJE klasę WCF zawierającą metody serwera proxy klienta, które uzyskują dostęp do operacji usługi sieci Web.

Podobnie jak w przypadku narzędzi [**metadanych Svcutil modelu usług**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) dla projektów .NET Framework, **dotnet-Svcutil** to narzędzie wiersza polecenia do generowania odwołania usługi internetowej zgodnej z projektami .NET Core i .NET Standard.

Narzędzie **dotnet-Svcutil** jest alternatywną opcją dla [**usługi sieci Web programu WCF odwołującej**](wcf-web-service-reference-guide.md) się do dostawcy usługi połączonej programu Visual Studio, która jest najpierw dostarczana z programem Visual studio 2017 w wersji 15,5. Narzędzie **dotnet-Svcutil** jako narzędzie .NET jest dostępne dla wielu platform w systemach Linux, MacOS i Windows.

> [!IMPORTANT]
> Należy tylko odwoływać się do usług z zaufanego źródła. Dodanie odwołań z niezaufanego źródła może spowodować naruszenie zabezpieczeń.

## <a name="prerequisites"></a>Wymagania wstępne

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

- [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) lub nowsza wersja
- Ulubiony Edytor kodu

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

- [.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) lub jego nowsze wersje
- Ulubiony Edytor kodu

---

## <a name="getting-started"></a>Wprowadzenie

Poniższy przykład przeprowadzi Cię przez kroki wymagane do dodania odwołania usługi sieci Web do projektu sieci Web platformy .NET Core i wywołania usługi. Utworzysz aplikację sieci Web platformy .NET Core o nazwie *HelloSvcutil* i dodasz odwołanie do usługi sieci Web, która implementuje następujący kontrakt:

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

Na potrzeby tego przykładu Załóżmy, że usługa sieci Web będzie hostowana pod następującym adresem: `http://contoso.com/SayHello.svc`

W oknie polecenia systemu Windows, macOS lub Linux wykonaj następujące czynności:

1. Utwórz katalog o nazwie _HelloSvcutil_ dla projektu i ustaw go jako bieżący katalog, tak jak w poniższym przykładzie:

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. Utwórz nowy C# projekt sieci Web w tym katalogu przy użyciu polecenia [`dotnet new`](../tools/dotnet-new.md) w następujący sposób:

    ```dotnetcli
    dotnet new web
    ```

3. Zainstaluj [pakiet NuGet`dotnet-svcutil`](https://nuget.org/packages/dotnet-svcutil) jako narzędzie interfejsu wiersza polecenia:  <!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)
    Otwórz plik projektu `HelloSvcutil.csproj` w edytorze, Edytuj element `Project` i Dodaj [pakiet NuGet`dotnet-svcutil`](https://nuget.org/packages/dotnet-svcutil) jako odwołanie narzędzia interfejsu wiersza polecenia, używając następującego kodu:

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    Następnie Przywróć pakiet _dotnet-Svcutil_ przy użyciu polecenia [`dotnet restore`](../tools/dotnet-restore.md) w następujący sposób:

    ```dotnetcli
    dotnet restore
    ```

    ---

4. Uruchom polecenie _dotnet-Svcutil_ , aby wygenerować plik referencyjny usługi sieci Web w następujący sposób:

    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

    ```dotnetcli
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

Wygenerowany plik zostanie zapisany jako _HelloSvcutil/ServiceReference/Reference. cs_. Narzędzie _dotnet-Svcutil_ dodaje również do projektu odpowiednie pakiety WCF wymagane przez kod serwera proxy jako odwołania do pakietu.

## <a name="using-the-service-reference"></a>Korzystanie z odwołania do usługi

1. Przywróć pakiety WCF przy użyciu [`dotnet restore`](../tools/dotnet-restore.md) polecenia w następujący sposób:

    ```dotnetcli
    dotnet restore
    ```

2. Znajdź nazwę klasy klienta i operację, której chcesz użyć. `Reference.cs` będzie zawierać klasę, która dziedziczy po `System.ServiceModel.ClientBase`, przy użyciu metod, które mogą być używane do wywoływania operacji w usłudze. W tym przykładzie chcesz wywołać operację _Hello_ usługi _sayHello_ . `ServiceReference.SayHelloClient` jest nazwą klasy klienta i ma metodę o nazwie `HelloAsync`, której można użyć do wywołania operacji.

3. Otwórz plik `Startup.cs` w edytorze i Dodaj instrukcję using dla przestrzeni nazw odwołania do usługi u góry:

    ```csharp
    using ServiceReference;
    ```

4. Edytuj metodę `Configure`, aby wywołać usługę sieci Web. Można to zrobić przez utworzenie wystąpienia klasy, która dziedziczy po `ClientBase` i wywołanie metody na obiekcie klienta:

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

5. Uruchom aplikację przy użyciu [`dotnet run`](../tools/dotnet-run.md) polecenia w następujący sposób:

    ```dotnetcli
    dotnet run
    ```

6. Przejdź do adresu URL podanego w konsoli programu (na przykład `http://localhost:5000`) w przeglądarce internetowej.

Powinny zostać wyświetlone następujące dane wyjściowe: "Hello dotnet-Svcutil!"

Aby uzyskać szczegółowy opis parametrów narzędzia `dotnet-svcutil`, wywołaj narzędzie do przekazywania parametru pomocy w następujący sposób:
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

```dotnetcli
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

```dotnetcli
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a>Opinie & pytania

Jeśli masz jakieś pytania lub opinie, [Otwórz problem w usłudze GitHub](https://github.com/dotnet/wcf/issues/new). Możesz również zapoznać się z istniejącymi pytaniami i problemami [w REPOZYTORIUM WCF w serwisie GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

## <a name="release-notes"></a>Uwagi do wersji

- Zapoznaj się z informacjami o [wersji](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) dotyczącymi zaktualizowanych informacji o wersji, w tym znanych problemów.

## <a name="information"></a>Informacje programu

- [Pakiet NuGet dotnet-Svcutil](https://nuget.org/packages/dotnet-svcutil)
