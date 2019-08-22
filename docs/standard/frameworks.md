---
title: Platformy docelowe
description: Dowiedz się więcej na temat platform docelowych dla aplikacji i bibliotek platformy .NET Core.
author: richlander
ms.author: mairaw
ms.date: 04/02/2019
ms.custom: updateeachrelease
ms.technology: dotnet-standard
ms.openlocfilehash: 20b13bb590a63a807c1894bf08051053f90c0fc4
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666520"
---
# <a name="target-frameworks"></a>Platformy docelowe

Gdy docelowa jest struktura w aplikacji lub bibliotece, określasz zestaw interfejsów API, które mają być dostępne dla aplikacji lub biblioteki. Należy określić platformę docelową w pliku projektu przy użyciu monikerów platformy docelowej (TFMs).

Aplikacja lub biblioteka może być ukierunkowana na wersję [.NET Standard](net-standard.md). Wersje .NET Standard reprezentują standardowe zestawy interfejsów API we wszystkich implementacjach platformy .NET. Na przykład biblioteka może kierować do .NET Standard 1,6 i uzyskać dostęp do interfejsów API, które działają w ramach platformy .NET Core i .NET Framework przy użyciu tej samej bazy kodu.

W celu uzyskania dostępu do interfejsów API specyficznych dla implementacji aplikacja lub biblioteka może być również ukierunkowana na określoną implementację platformy .NET. Przykładowo aplikacja, która jest przeznaczona dla platformy Xamarin. iOS (na `Xamarin.iOS10`przykład), uzyskuje dostęp do otok interfejsów API systemu iOS dla systemu iOS 10 lub aplikację, która jest przeznaczona dla platforma uniwersalna systemu Windows ( `uap10.0`platformy UWP), ma dostęp do interfejsu API kompilowanego dla urządzeń z systemem System Windows 10.

W przypadku niektórych platform docelowych (na przykład .NET Framework) interfejsy API są definiowane przez Zestawy instalowane przez platformę w systemie i mogą zawierać interfejsy API struktury aplikacji (na przykład ASP.NET).

W przypadku platform docelowych opartych na pakietach (na przykład .NET Standard i .NET Core) interfejsy API są definiowane przez pakiety zawarte w aplikacji lub bibliotece. Pakiet jest pakietem NuGet, który nie ma własnej zawartości, ale jest listą zależności (inne pakiety). Platforma docelowa oparta na pakiecie NuGet niejawnie określa pakiet, który odwołuje się do wszystkich pakietów, które razem tworzą strukturę.

## <a name="latest-target-framework-versions"></a>Najnowsze wersje platformy docelowej

Poniższa tabela zawiera definicje najpopularniejszych platform docelowych, sposobu ich odwoływania oraz wersji zaimplementowanych [.NET Standard](net-standard.md) . Te wersje platformy docelowej są najnowszymi stabilnymi wersjami. Wersje wstępne nie są wyświetlane. Moniker platformy docelowej (TFM) to standardowy format tokenu służący do określania docelowej platformy aplikacji lub biblioteki platformy .NET.

| Struktura docelowa      | Najnowsza <br/> Stabilna wersja | Moniker platformy docelowej (TFM) | Realizowane <br/> Wersja .NET Standard |
| :-------------------: | :-------------------------: | :----------------------------: | :-------------------------------------: |
| .NET Standard         | 2.0                         | netstandard2.0                 | Brak                                     |
| .NET Core             | 2.2                         | netcoreapp 2.2                  | 2.0                                     |
| .NET Framework        | 4.8                         | net48                          | 2.0                                     |

## <a name="supported-target-framework-versions"></a>Obsługiwane wersje platformy docelowej

Platforma docelowa jest zwykle przywoływana przez TFM. W poniższej tabeli przedstawiono Platformy docelowe obsługiwane przez zestaw .NET Core SDK i klienta NuGet. Odpowiedniki są wyświetlane w nawiasach kwadratowych. Na przykład, `win81` jest odpowiednikiem TFM do `netcore451`.

| Struktura docelowa           | TFM |
| -------------------------- | --- |
| .NET Standard              | Standard 1.0<br>Standard 1.1<br>Standard 1.2<br>Standard 1.3<br>Standardowa 1.4<br>Standard 1.5<br>Standard 1.6<br>netstandard2.0 |
| .NET Core                  | netcoreapp 1.0<br>netcoreapp 1.1<br>netcoreapp 2.0<br>netcoreapp 2.1<br>netcoreapp 2.2 |
| .NET Framework             | net11<br>net20<br>net35<br>net40<br>net403<br>net45<br>net451<br>net452<br>net46<br>net461<br>net462<br>net47<br>net471<br>net472<br>net48 |
| Sklep Windows              | Rdzeń [netcore45]<br>netcore45 [win] [Win8]<br>netcore451 [Win81] |
| .NET Micro Framework       | netmf |
| Silverlight                | sl4<br>sl5 |
| Windows Phone              | WP [WP7]<br>wp7<br>wp75<br>wp8<br>wp81<br>wpa81 |
| Platforma uniwersalna systemu Windows | UAP [UAP 10.0]<br>UAP 10.0 [Win10] [netcore50] |

## <a name="how-to-specify-target-frameworks"></a>Jak określić Platformy docelowe

Struktury docelowe są określone w pliku projektu. W przypadku określenia pojedynczej platformy docelowej należy użyć elementu **TargetFramework** . Poniższy plik projektu aplikacji konsolowej pokazuje, jak kierować platformą .NET Core 2,2:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>
  </PropertyGroup>

</Project>
```

W przypadku określania wielu platform docelowych można warunkowo odwoływać się do zestawów dla każdej platformy docelowej. W kodzie można warunkowo kompilować do tych zestawów przy użyciu symboli preprocesora z logiką *if-then-else* .

Następujący plik projektu biblioteki kieruje interfejsy API .NET Standard (`netstandard1.4`) i interfejsów API .NET Framework (`net40` i `net45`). Użyj elementu **TargetFrameworks** w liczbie mnogiej z wieloma platformami docelowymi. Należy pamiętać, `Condition` że atrybuty obejmują pakiety specyficzne dla implementacji, gdy biblioteka jest skompilowana dla dwóch .NET Framework TFMs:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Conditionally obtain references for the .NET Framework 4.0 target -->
  <ItemGroup Condition=" '$(TargetFramework)' == 'net40' ">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Conditionally obtain references for the .NET Framework 4.5 target -->
  <ItemGroup Condition=" '$(TargetFramework)' == 'net45' ">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>

</Project>
```

W Twojej bibliotece lub aplikacji napiszesz kod warunkowy do skompilowania dla każdej platformy docelowej:

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        Console.WriteLine("Target framework: .NET Framework 4.0");
#elif NET45  
        Console.WriteLine("Target framework: .NET Framework 4.5");
#else
        Console.WriteLine("Target framework: .NET Standard 1.4");
#endif
    }
}
```

System kompilacji ma świadomość symboli preprocesora reprezentujących Platformy docelowe wyświetlane w tabeli [obsługiwane wersje platformy docelowej](#supported-target-framework-versions) . Przy użyciu symbolu, który reprezentuje .NET Standard lub TFM .NET Core, Zastąp kropkę znakiem podkreślenia i Zmień małe litery na wielkie litery (na przykład symbol dla elementu `netstandard1.4` `NETSTANDARD1_4`).

Kompletna lista symboli preprocesora dla platform .NET Core Target Framework to:

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a>Przestarzałe Platformy docelowe

Poniższe Platformy docelowe są przestarzałe. Pakiety przeznaczone dla tych platform docelowych powinny migrować do wskazanych elementów zastępczych.

| Przestarzałe TFM                                                                             | Zastępc |
| ------------------------------------------------------------------------------------------ | ----------- |
| aspnet50<br>aspnetcore50<br>dnxcore50<br>dnx<br>dnx45<br>dnx451<br>dnx452                  | netcoreapp  |
| dotnet<br>dotnet50<br>dotnet51<br>dotnet52<br>dotnet53<br>dotnet54<br>dotnet55<br>dotnet56 | netstandard |
| netcore50                                                                                  | UAP 10.0     |
| kupione                                                                                        | netcore45   |
| Win8                                                                                       | netcore45   |
| win81                                                                                      | netcore451  |
| Win10                                                                                      | UAP 10.0     |
| winrt                                                                                      | netcore45   |

## <a name="see-also"></a>Zobacz także

- [Pakiety, metapakiety i struktury](../core/packages.md)
- [Tworzenie bibliotek za pomocą narzędzi międzyplatformowych](../core/tutorials/libraries.md)
- [.NET Standard](net-standard.md)
- [Obsługa wersji platformy .NET Core](../core/versions/index.md)
- [repozytorium dotnet/standardowe usługi GitHub](https://github.com/dotnet/standard)
- [Repozytorium GitHub narzędzi NuGet](https://github.com/joelverhagen/NuGetTools)
- [Profile struktury w programie .NET](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html)
