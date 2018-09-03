---
title: Narzędzia dotnet svcutil Microsoft WCF
description: Omówienie narzędzia dotnet svcutil Microsoft WCF, który dodaje funkcje dla projektów .NET Core i ASP.NET Core, podobny do narzędzia svcutil WCF dla projektów programu .NET Framework.
author: mlacouture
ms.author: jralexander
ms.date: 08/20/2018
ms.openlocfilehash: bb4d8e5f3997318b720535b0f1e07fc33d13338a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484124"
---
# <a name="microsoft-wcf-dotnet-svcutil-tool"></a>Narzędzia dotnet svcutil Microsoft WCF

Windows Communication Foundation (WCF) **narzędzia svcutil dotnet** narzędzie to narzędzie wiersza polecenia platformy .NET Core, pobiera metadane z usługi sieci web w lokalizacji sieciowej lub z pliku WSDL, która generuje klasę usługi WCF, zawierająca metody serwera proxy klienta, dostęp do operacji usługi sieci web.

Podobnie jak [ **metadanych modelu usługi - svcutil** ](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia dla projektów programu .NET Framework **narzędzia svcutil dotnet** jest narzędziem wiersza polecenia do generowania odwołanie do usługi sieci web zgodne z projektami .NET Core i .NET Standard.

**Narzędzia svcutil dotnet** narzędzie jest alternatywnych opcji [ **WCF Web Service Reference** ](wcf-web-service-reference-guide.md) dostawcy usług, które po raz pierwszy wysłane połączona programu Visual Studio z programem Visual Studio v15.5 2017 r. **Narzędzia svcutil dotnet** narzędzia jako narzędzie wiersza polecenia platformy .NET Core, są dostępne dla wielu platform w systemie Linux, macOS i Windows.

> [!IMPORTANT]
> Użytkownik powinien odwoływać się tylko do usług z zaufanego źródła. Dodawanie odwołań z niezaufanego źródła może naruszyć bezpieczeństwo.

## <a name="prerequisites"></a>Wymagania wstępne

* [Zestaw .NET core SDK](https://www.microsoft.com/net/download) v1.0.4 lub nowsze wersje
* Wybrany edytor kodu

## <a name="getting-started"></a>Wprowadzenie

Poniższy przykład przeprowadzi Cię przez kroki wymagane do Dodaj odwołanie do usługi sieci web, aby projekt konsoli .NET Core i wywołać usługę. Utworzysz aplikację konsolową .NET Core, o nazwie _HelloSvcutil_ i doda odwołanie do usługi sieci web, który implementuje ten kontrakt następujące:

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

W tym przykładzie Usługa sieci web zostanie przyjęta wartość będzie hostowana pod następującym adresem: `http://contoso.com/SayHello.svc`

Z poziomu okna polecenia Windows, macOS lub Linux, wykonaj następujące czynności:

1. Utwórz katalog o nazwie _HelloSvcutil_ dla projektu i udostępnić go w bieżącym katalogu, jak w poniższym przykładzie:

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. Utwórz nowy projekt konsoli języka C#, w tym katalogu przy użyciu [ `dotnet new` ](../tools/dotnet-new.md) polecenia w następujący sposób:

```console
dotnet new console
```

3. Otwórz `HelloSvcutil.csproj` projektu plik w edytorze, Edytuj `Project` element i Dodaj [ `dotnet-svcutil` pakietu NuGet](https://nuget.org/packages/dotnet-svcutil) jako odwołanie narzędzie interfejsu wiersza polecenia, używając następującego kodu:

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
</ItemGroup>
```

4. Przywróć _narzędzia svcutil dotnet_ pakietu przy użyciu [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia w następujący sposób:

```console
dotnet restore
```

5. Uruchom _dotnet_ z _svcutil_ polecenie, aby wygenerować plik odwołanie do usługi sieci web w następujący sposób:

```console
dotnet svcutil http://contoso.com/SayHello.svc
```
Wygenerowany plik jest zapisywany jako _HelloSvcutil/ServiceReference1/Reference.cs_. _Dotnet_svcutil_ narzędzie automatycznie dodaje również do projektu odpowiednich pakietów WCF wymagane przez kod serwera proxy jako odwołania do pakietu.

6. Przywróć pakiety programu WCF za pomocą [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia w następujący sposób:

```console
dotnet restore
```

7. Otwórz `Program.cs` plik w edytorze, Edytuj `Main()` metodę i Zastąp automatycznego generowania kodu za pomocą następującego kodu, aby wywołać usługę sieci web:

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
Powinien zostać wyświetlony następujący komunikat: "Hello narzędzia svcutil dotnet"!

Aby uzyskać szczegółowy opis `dotnet-svcutil` narzędzia parametrów, wywołaj narzędzie przekazywania parametru pomocy w następujący sposób:

```console
dotnet svcutil --help
```

## <a name="next-steps"></a>Następne kroki

### <a name="feedback--questions"></a>Opinie i pytania

Jeśli masz pytania lub opinie, [Otwórz problem w serwisie GitHub](https://github.com/dotnet/wcf/issues/new). Możesz również sprawdzić wszelkie istniejące pytania lub problemy [w repozytorium usługi WCF w usłudze GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

### <a name="release-notes"></a>Uwagi do wersji

* Zapoznaj się [informacje o wersji](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) uzyskać informacje o zaktualizowanej wersji, w tym znanych problemów.

### <a name="information"></a>Informacje

* [Pakiet NuGet narzędzia svcutil DotNet](https://nuget.org/packages/dotnet-svcutil)
