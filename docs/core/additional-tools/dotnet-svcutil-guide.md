---
title: Omówienie narzędzia svcutil WCF
description: Omówienie narzędzia dotnet svcutil Microsoft WCF, który dodaje funkcje dla projektów .NET Core i ASP.NET Core, podobny do narzędzia svcutil WCF dla projektów programu .NET Framework.
author: mlacouture
ms.date: 02/22/2019
ms.custom: seodec18
ms.openlocfilehash: 5e361ce85bec696fe5d76c4f43a444c543a9012d
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063290"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a>Narzędzia dotnet svcutil WCF dla platformy .NET Core

Windows Communication Foundation (WCF) **narzędzia svcutil dotnet** narzędzie to narzędzie wiersza polecenia platformy .NET Core, pobiera metadane z usługi sieci web w lokalizacji sieciowej lub z pliku WSDL, która generuje klasę usługi WCF, zawierająca metody serwera proxy klienta, dostęp do operacji usługi sieci web.

Podobnie jak [ **metadanych modelu usługi - svcutil** ](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia dla projektów programu .NET Framework **narzędzia svcutil dotnet** jest narzędziem wiersza polecenia do generowania odwołanie do usługi sieci web zgodne z projektami .NET Core i .NET Standard.

**Narzędzia svcutil dotnet** narzędzie jest alternatywnych opcji [ **WCF Web Service Reference** ](wcf-web-service-reference-guide.md) dostawcy usług, które po raz pierwszy wysłane połączona programu Visual Studio z programem Visual Studio v15.5 2017 r. **Narzędzia svcutil dotnet** narzędzia jako narzędzie wiersza polecenia platformy .NET Core, są dostępne dla wielu platform w systemie Linux, macOS i Windows.

> [!IMPORTANT]
> Użytkownik powinien odwoływać się tylko do usług z zaufanego źródła. Dodawanie odwołań z niezaufanego źródła może naruszyć bezpieczeństwo.

## <a name="prerequisites"></a>Wymagania wstępne

# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)
* [Zestaw SDK programu .NET core 2.1](https://dotnet.microsoft.com/download) lub nowsze wersje
* Wybrany edytor kodu

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)
* [.NET core 1.0.4 SDK](https://dotnet.microsoft.com/download) lub nowsze wersje
* Wybrany edytor kodu

---

## <a name="getting-started"></a>Wprowadzenie

Poniższy przykład przeprowadzi Cię przez kroki wymagane do Dodaj odwołanie do usługi sieci web do projektu sieci web platformy .NET Core i wywołać usługę. Utworzysz aplikację sieci web platformy .NET Core, o nazwie _HelloSvcutil_ i Dodaj odwołanie do usługi sieci web, który implementuje ten kontrakt następujące:

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

W tym przykładzie załóżmy, że będzie hostowana usługa sieci web, korzystając z następującego adresu: `http://contoso.com/SayHello.svc`

Z poziomu okna polecenia Windows, macOS lub Linux, wykonaj następujące czynności:

1. Utwórz katalog o nazwie _HelloSvcutil_ dla projektu i udostępnić go w bieżącym katalogu, jak w poniższym przykładzie:

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. Utwórz nową C# projektu sieci web w tym katalogu przy użyciu [ `dotnet new` ](../tools/dotnet-new.md) polecenia w następujący sposób:

    ```console
    dotnet new web
    ```

3. Zainstaluj [ `dotnet-svcutil` pakietu NuGet](https://nuget.org/packages/dotnet-svcutil) jako narzędzie interfejsu wiersza polecenia:  <!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```console
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)
    Otwórz `HelloSvcutil.csproj` projektu plik w edytorze, Edytuj `Project` element i Dodaj [ `dotnet-svcutil` pakietu NuGet](https://nuget.org/packages/dotnet-svcutil) jako odwołanie narzędzie interfejsu wiersza polecenia, używając następującego kodu:

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    Następnie Przywróć _narzędzia svcutil dotnet_ pakietu przy użyciu [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia w następujący sposób:

    ```console
    dotnet restore
    ```

    ---

4. Uruchom _narzędzia svcutil dotnet_ polecenie, aby wygenerować plik odwołanie do usługi sieci web w następujący sposób:

    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```console
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

    ```console
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

Wygenerowany plik jest zapisywany jako _HelloSvcutil/ServiceReference/Reference.cs_. _Narzędzia svcutil dotnet_ narzędzie automatycznie dodaje również do projektu odpowiednich pakietów WCF wymagane przez kod serwera proxy jako odwołania do pakietu.

## <a name="using-the-service-reference"></a>Za pomocą odwołania do usługi

1. Przywróć pakiety programu WCF za pomocą [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia w następujący sposób:

    ```console
    dotnet restore
    ```

2. Znajdź nazwę klienta, klasy i operacji, które chcesz użyć. `Reference.cs` zawiera klasy, która dziedziczy `System.ServiceModel.ClientBase`, za pomocą metod, które mogą służyć do wywoływania operacji w usłudze. W tym przykładzie, który chcesz wybrać _SayHello_ usługi _Hello_ operacji. `ServiceReference.SayHelloClient` jest nazwą Klasa klienta i metody o nazwie `HelloAsync` można wywołać operację.

3. Otwórz `Startup.cs` plik w edytorze i Dodaj instrukcję using instrukcji dla przestrzeni nazw odwołań usługi u góry:

    ```csharp
    using ServiceReference;
    ```

4. Edytuj `Configure` metody do wywołania usługi sieci web. Możesz to zrobić przez utworzenie wystąpienia klasy, która dziedziczy `ClientBase` i wywołanie metody w obiekcie klienta:

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

5. Uruchamianie aplikacji przy użyciu [ `dotnet run` ](../tools/dotnet-run.md) polecenia w następujący sposób:

    ```console
    dotnet run
    ```

6. Przejdź do adresu URL podanego w konsoli (na przykład `http://localhost:5000`) w przeglądarce sieci web.

Powinny zostać wyświetlone następujące dane wyjściowe: "Hello dotnet-svcutil /!"

Aby uzyskać szczegółowy opis `dotnet-svcutil` narzędzia parametrów, wywołaj narzędzie przekazywania parametru pomocy w następujący sposób:
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

```console
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

```console
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a>Opinie i pytania

Jeśli masz pytania lub opinie, [Otwórz problem w serwisie GitHub](https://github.com/dotnet/wcf/issues/new). Możesz również sprawdzić wszelkie istniejące pytania lub problemy [w repozytorium usługi WCF w usłudze GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

## <a name="release-notes"></a>Uwagi do wersji

* Zapoznaj się [informacje o wersji](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) uzyskać informacje o zaktualizowanej wersji, w tym znanych problemów.

## <a name="information"></a>Informacje

* [Pakiet NuGet narzędzia svcutil DotNet](https://nuget.org/packages/dotnet-svcutil)
