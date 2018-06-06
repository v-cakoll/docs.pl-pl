---
title: Narzędzia dotnet svcutil Microsoft WCF
description: Omówienie narzędzia dotnet svcutil Microsoft WCF, który dodaje funkcje platformy .NET Core i ASP.NET Core projektów, podobnie jak narzędzia svcutil WCF dla projektów .NET Framework.
author: mlacouture
ms.author: jralexander
ms.date: 06/04/2018
ms.openlocfilehash: c40dd9b437afe7381244b944228b6b2efe046eb2
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753425"
---
# <a name="microsoft-wcf-dotnet-svcutil-tool"></a>Narzędzia dotnet svcutil Microsoft WCF

Windows Communication Foundation (WCF) **dotnet svcutil** narzędzie to narzędzie .NET Core interfejsu wiersza polecenia, które pobiera metadane z usługi sieci web w lokalizacji sieciowej lub z pliku WSDL, a następnie generuje WCF klasy zawierające metody serwera proxy klienta który dostęp do operacji usługi sieci web.

Podobnie jak [ **metadanych modelu usługi - svcutil** ](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzi dla projektów .NET Framework **dotnet svcutil** to narzędzie wiersza polecenia do generowania odwołania do usługi sieci web zgodny z projektów .NET Core i .NET Standard.

**Dotnet svcutil** narzędzie jest dostępna opcja alternatywnych [ **odwołania do usługi sieci Web WCF** ](wcf-web-service-reference-guide.md) programu Visual Studio połączenia usługodawcy, najpierw dostarczonej z programem Visual Studio v15.5 2017 r. **Dotnet svcutil** narzędzie jako narzędzie .NET Core interfejsu wiersza polecenia, jest dostępny i platform w systemie Linux, macOS i systemu Windows.

> [!IMPORTANT]
> Użytkownik powinien odwoływać się tylko usługi z zaufanego źródła. Dodawanie odwołań z niezaufanego źródła może naruszyć bezpieczeństwo.

## <a name="prerequisites"></a>Wymagania wstępne

* [Zestaw SDK programu .NET core](https://www.microsoft.com/net/download) v1.0.4 lub nowszy
* Edytor kodu ulubionych

## <a name="getting-started"></a>Wprowadzenie

Poniższy przykład przeprowadzi Cię przez kroki wymagane do dodawania odwołania do usługi sieci web do projektu konsoli .NET Core i wywoływanie usługi. Spowoduje utworzenie aplikacji konsoli .NET Core o nazwie _HelloSvcutil_ oraz zostanie dodane odwołanie do usługi sieci web implementujący kontrakt następujące:

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

Na przykład usługi sieci web będzie traktowane jako hostowany pod następującym adresem: `http://contoso.com/SayHello.svc`

W oknie polecenia systemu Windows, system macOS lub Linux, wykonaj następujące czynności:

1. Utwórz katalog o nazwie _HelloSvcutil_ dla projektu i przekształcenie go w bieżącym katalogu, jak w poniższym przykładzie:

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. Utwórz nowy projekt console C# w tym katalogu przy użyciu [ `dotnet new` ](../tools/dotnet-new.md) polecenia w następujący sposób:

```console
dotnet new console
```

3. Otwórz `HelloSvcutil.csproj` projekt plik w edytorze, Edytuj `Project` element i Dodaj [ `dotnet-svcutil` pakietu NuGet](https://nuget.org/packages/dotnet-svcutil) jako odwołanie narzędzia interfejsu wiersza polecenia, używając następującego kodu:

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.0" />
</ItemGroup>
```

4. Przywróć _dotnet svcutil_ pakietu przy użyciu [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia w następujący sposób:

```console
dotnet restore
```

5. Uruchom _dotnet_ z _svcutil_ polecenie w celu wygenerowania pliku odwołań do usługi sieci web w następujący sposób:

```console
dotnet svcutil http://contoso.com/SayHello.svc
```
Wygenerowany plik zostanie zapisany jako _HelloSvcutil/ServiceReference1/Reference.cs_. _Dotnet_svcutil_ narzędzie również dodaje do projektu odpowiednich pakietów WCF wymagane przez kod serwera proxy jako odwołania do pakietu.

6. Przywracanie pakietów WCF za pomocą [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia w następujący sposób:

```console
dotnet restore
```

7. Otwórz `Program.cs` plik w edytorze, Edytuj `Main()` metodę i Zastąp automatycznego generowania kodu przy użyciu następujący kod, aby wywołać usługę sieci web:

```csharp
static void Main(string[] args)
{
    var client = new SayHelloClient();
    Console.WriteLine(client.HelloAsync("dotnet-svcutil").Result);
}
```

8. Uruchamianie aplikacji przy użyciu [ `dotnet run` ](../tools/dotnet-run.md) polecenia w następujący sposób:

```console
dotnet run
```
Powinny pojawić się następujące dane wyjściowe: "tekst Hello dotnet svcutil!"

Aby uzyskać szczegółowy opis `dotnet-svcutil` narzędzie parametrów, wywołania narzędzia przekazywanie parametru pomocy w następujący sposób:

```console
dotnet svcutil --help
```

## <a name="next-steps"></a>Następne kroki

### <a name="feedback--questions"></a>Opinie i pytania

Jeśli masz pytania lub opinie, [Otwórz problemu w serwisie GitHub](https://github.com/dotnet/wcf/issues/new). Można także przejrzeć wszystkie istniejące pytania lub problemy [w repozytorium usługi WCF w usłudze GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

### <a name="release-notes"></a>Uwagi do wersji

* Zapoznaj się [informacje o wersji](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) uzyskać informacje o zaktualizowanej wersji, w tym znanych problemów.

### <a name="information"></a>Informacje

* [Pakiet NuGet DotNet svcutil](https://nuget.org/packages/dotnet-svcutil)
