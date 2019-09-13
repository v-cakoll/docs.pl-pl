---
title: Omówienie narzędzia WCF Svcutil
description: Omówienie narzędzia dotnet-Svcutil programu Microsoft WCF, które dodaje funkcje dla projektów .NET Core i ASP.NET Core, podobnie jak narzędzie WCF Svcutil dla projektów .NET Framework.
author: mlacouture
ms.date: 02/22/2019
ms.custom: seodec18
ms.openlocfilehash: 723855401f3a81edbd34c77481e4ff12db7dcdaf
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926451"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a>WCF dotnet-Svcutil Tool dla platformy .NET Core

Windows Communication Foundation (WCF) **dotnet-Svcutil** Tool to narzędzie interfejs wiersza polecenia platformy .NET Core, które pobiera metadane z usługi sieci Web w lokalizacji sieciowej lub z pliku WSDL, i GENERUJE klasę WCF zawierającą metody serwera proxy klienta, które uzyskują dostęp do usługi sieci Web. składowa.

Podobnie jak w przypadku narzędzi [**metadanych Svcutil modelu usług**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) dla projektów .NET Framework, **dotnet-Svcutil** to narzędzie wiersza polecenia do generowania odwołania usługi internetowej zgodnej z projektami .NET Core i .NET Standard.

Narzędzie **dotnet-Svcutil** jest alternatywną opcją dla [**usługi sieci Web programu WCF odwołującej**](wcf-web-service-reference-guide.md) się do dostawcy usługi połączonej programu Visual Studio, która jest najpierw dostarczana z programem Visual Studio 2017 v 15.5. Narzędzie **dotnet-Svcutil** jako narzędzie interfejs wiersza polecenia platformy .NET Core jest dostępne dla wielu platform w systemach Linux, MacOS i Windows.

> [!IMPORTANT]
> Należy tylko odwoływać się do usług z zaufanego źródła. Dodanie odwołań z niezaufanego źródła może spowodować naruszenie zabezpieczeń.

## <a name="prerequisites"></a>Wymagania wstępne

# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

* [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) lub nowsza wersja
* Ulubiony Edytor kodu

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

* [.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) lub jego nowsze wersje
* Ulubiony Edytor kodu

---

## <a name="getting-started"></a>Wprowadzenie

Poniższy przykład przeprowadzi Cię przez kroki wymagane do dodania odwołania usługi sieci Web do projektu sieci Web platformy .NET Core i wywołania usługi. Utworzysz aplikację sieci Web platformy .NET Core o nazwie _HelloSvcutil_ i dodasz odwołanie do usługi sieci Web, która implementuje następujący kontrakt:

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

Na potrzeby tego przykładu Załóżmy, że usługa sieci Web będzie hostowana pod następującym adresem:`http://contoso.com/SayHello.svc`

W oknie polecenia systemu Windows, macOS lub Linux wykonaj następujące czynności:

1. Utwórz katalog o nazwie _HelloSvcutil_ dla projektu i ustaw go jako bieżący katalog, tak jak w poniższym przykładzie:

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. Utwórz nowy C# projekt sieci Web w tym katalogu przy użyciu [`dotnet new`](../tools/dotnet-new.md) polecenia w następujący sposób:

    ```console
    dotnet new web
    ```

3. Zainstaluj pakiet NuGet jako narzędzie interfejsu wiersza polecenia: [ `dotnet-svcutil` ](https://nuget.org/packages/dotnet-svcutil) <!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```console
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)
    Otwórz plik [ `dotnet-svcutil` ](https://nuget.org/packages/dotnet-svcutil) projektu w edytorze, `Project` Edytuj element i Dodaj pakiet NuGet jako odwołanie narzędzia interfejsu wiersza polecenia, używając następującego kodu: `HelloSvcutil.csproj`

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    Następnie Przywróć pakiet _dotnet-Svcutil_ za pomocą [`dotnet restore`](../tools/dotnet-restore.md) polecenia w następujący sposób:

    ```console
    dotnet restore
    ```

    ---

4. Uruchom polecenie _dotnet-Svcutil_ , aby wygenerować plik referencyjny usługi sieci Web w następujący sposób:

    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```console
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

    ```console
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

Wygenerowany plik zostanie zapisany jako _HelloSvcutil/ServiceReference/Reference. cs_. Narzędzie _dotnet-Svcutil_ dodaje również do projektu odpowiednie pakiety WCF wymagane przez kod serwera proxy jako odwołania do pakietu.

## <a name="using-the-service-reference"></a>Korzystanie z odwołania do usługi

1. Przywróć pakiety WCF przy użyciu [`dotnet restore`](../tools/dotnet-restore.md) polecenia w następujący sposób:

    ```console
    dotnet restore
    ```

2. Znajdź nazwę klasy klienta i operację, której chcesz użyć. `Reference.cs`będzie zawierać klasę, która dziedziczy z `System.ServiceModel.ClientBase`, przy użyciu metod, które mogą być używane do wywoływania operacji w usłudze. W tym przykładzie chcesz wywołać operację _Hello_ usługi _sayHello_ . `ServiceReference.SayHelloClient`jest nazwą klasy klienta i ma metodę o nazwie `HelloAsync` , która może być używana do wywołania operacji.

3. `Startup.cs` Otwórz plik w edytorze i Dodaj instrukcję using dla przestrzeni nazw odwołania do usługi u góry:

    ```csharp
    using ServiceReference;
    ```

4. `Configure` Edytuj metodę, aby wywołać usługę sieci Web. Można to zrobić, tworząc wystąpienie klasy, która dziedziczy z `ClientBase` i wywołując metodę na obiekcie klienta:

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

5. Uruchom aplikację za pomocą [`dotnet run`](../tools/dotnet-run.md) polecenia w następujący sposób:

    ```console
    dotnet run
    ```

6. Przejdź do adresu URL podanego w konsoli programu (na `http://localhost:5000`przykład) w przeglądarce sieci Web.

Powinny zostać wyświetlone następujące dane wyjściowe: "Hello dotnet-Svcutil!"

Aby uzyskać szczegółowy opis `dotnet-svcutil` parametrów narzędzia, wywołaj narzędzie do przekazywania parametru pomocy w następujący sposób:
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

```console
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

```console
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a>Opinie & pytania

Jeśli masz jakieś pytania lub opinie, [Otwórz problem w usłudze GitHub](https://github.com/dotnet/wcf/issues/new). Możesz również zapoznać się z istniejącymi pytaniami i problemami [w REPOZYTORIUM WCF w serwisie GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

## <a name="release-notes"></a>Uwagi do wersji

* Zapoznaj się z informacjami o [wersji](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) dotyczącymi zaktualizowanych informacji o wersji, w tym znanych problemów.

## <a name="information"></a>Informacje

* [Pakiet NuGet dotnet-Svcutil](https://nuget.org/packages/dotnet-svcutil)
