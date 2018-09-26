---
title: Platformy docelowe
description: Więcej informacji na temat platform docelowych dla aplikacji platformy .NET Core i bibliotek.
author: richlander
ms.author: mairaw
ms.date: 05/31/2018
ms.custom: updateeachrelease
ms.technology: dotnet-standard
ms.openlocfilehash: 76bf496e957022f4d97d3cf3f3975f334b1d5c45
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47204417"
---
# <a name="target-frameworks"></a>Platformy docelowe

Gdy miejscem docelowym framework w aplikacji lub biblioteki można określać zestaw interfejsów API, który chcesz udostępnić aplikację lub bibliotekę. Należy określić platformę docelową w pliku projektu przy użyciu Target Framework monikerów (krótkich nazw).

Aplikacja lub biblioteka może odwoływać się do wersji [.NET Standard](~/docs/standard/net-standard.md). Wersje .NET standard reprezentują standardowe zestawy interfejsów API we wszystkich wdrożeniach platformy .NET. Na przykład biblioteka może docelowej platformy .NET Standard w wersji 1.6 i uzyskać dostęp do interfejsów API tej funkcji dla platformy .NET Core i .NET Framework przy użyciu tej samej bazy kodu.

Aplikacja lub biblioteka można również przeznaczać konkretnej implementacji .NET w celu uzyskania dostępu do interfejsów API specyficzne dla implementacji. Na przykład aplikację, która jest przeznaczony dla platformy Xamarin.iOS (na przykład `Xamarin.iOS10`) uzyskuje dostęp do otoki Xamarin — pod warunkiem interfejsów API systemu iOS dla systemu iOS 10 lub aplikację, który jest przeznaczony dla platformy uniwersalnej Windows (UWP, `uap10.0`) ma dostęp do interfejsów API, które kompilowanie dla urządzeń z systemem Windows 10.

Dla niektórych platform docelowych (na przykład, .NET Framework) interfejsy API są definiowane przez zestawy, że framework instaluje się w systemie i mogą zawierać struktury aplikacji interfejsów API (na przykład ASP.NET).

Dla platform docelowych na podstawie pakietu, (na przykład .NET Standard i .NET Core) interfejsy API są definiowane przez pakiety uwzględnione w aplikacji lub biblioteki. A *meta Microsoft.aspnetcore.all* pakietu NuGet, który nie ma zawartości z oddzielnie, ale jest listę zależności (inne pakiety). Platforma docelowa opartej na pakiecie NuGet określa niejawnie meta Microsoft.aspnetcore.all, który odwołuje się do wszystkich pakietów, które razem tworzą platformę.

## <a name="latest-target-framework-versions"></a>Najnowsza wersja wskazywać wersji struktury

W poniższej tabeli opisano najbardziej typowe platform docelowych, jak w przypadku odwołania i której wersji [.NET Standard](~/docs/standard/net-standard.md) implementują. Te target framework w wersji są najnowsze stabilne wersje. Wersje wstępne nie są wyświetlane. Moniker Framework docelowych (TFM) to standardowy format tokenu Określanie platformy docelowej aplikacji platformy .NET lub biblioteki.

| Platforma docelowa      | Najnowsza <br/> Stabilną wersję | Moniker platformy docelowej (TFM) | Zaimplementowany <br/> Wersja programu .NET standard |
| :-------------------: | :-------------------------: | :----------------------------: | :-------------------------------------: |
| .NET standard         | 2.0                         | netstandard2.0                 | Brak                                     |
| .NET Core             | 2.1                         | netcoreapp2.1                  | 2.0                                     |
| .NET Framework        | 4.7.2                       | net472                         | 2.0                                     |

## <a name="supported-target-framework-versions"></a>Obsługiwane target framework w wersji

Platforma docelowa jest zwykle przywoływany przez TFM. W poniższej tabeli przedstawiono platformy docelowe obsługiwane przez zestaw SDK programu .NET Core i klienta programu NuGet. Odpowiedniki są wyświetlane w nawiasach. Na przykład `win81` jest równoważne elementu TFM do `netcore451`.

| Platforma docelowa           | TFM |
| -------------------------- | --- |
| .NET standard              | netstandard1.0<br>netstandard1.1<br>netstandard1.2<br>netstandard1.3<br>netstandard1.4<br>netstandard1.5<br>netstandard1.6<br>netstandard2.0 |
| .NET Core                  | netcoreapp1.0<br>netcoreapp1.1<br>netcoreapp2.0<br>netcoreapp2.1 |
| .NET Framework             | net11<br>net20<br>net35<br>net40<br>net403<br>net45<br>net451<br>net452<br>net46<br>net461<br>net462<br>net47<br>net471<br>net472 |
| Sklep Windows              | netcore [netcore45]<br>netcore45 [win] [win8]<br>netcore451 [win81] |
| .NET Framework wczesnych       | netmf |
| Silverlight                | sl4<br>sl5 |
| Windows Phone              | WP [wp7]<br>wp7<br>wp75<br>wp8<br>wp81<br>wpa81 |
| Platforma uniwersalna systemu Windows | uap [uap10.0]<br>uap10.0 [Windows 10] [netcore50] |

## <a name="how-to-specify-target-frameworks"></a>Jak określić platform docelowych

Platformy docelowe są określone w pliku projektu. Kiedy struktura pojedynczy element docelowy jest określona, użyj **TargetFramework** elementu. Następujący plik projektu aplikacji konsoli Pokazuje, jak i docelowej platformy .NET Core 2.0:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Podczas określania wielu platform docelowych możesz warunkowo może odwoływać się zestawów dla każdej platformy docelowej. W kodzie, możesz warunkowo skompilować względem tych zestawów przy użyciu symboli preprocesora z *if-then-else* logiki.

Następujący plik projektu biblioteki jest przeznaczony dla interfejsów API programu .NET Standard (`netstandard1.4`) oraz interfejsów API programu .NET Framework (`net40` i `net45`). Użyj liczbę mnogą **TargetFrameworks** elementu z wielu platform docelowych. Uwaga jak `Condition` atrybuty zawierają specyficzne dla implementacji pakietów podczas kompilowania biblioteki dla dwóch .NET Framework krótkich nazw platform:

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

W bibliotece lub aplikacji piszesz kod warunkowy, aby skompilować dla każdej platformy docelowej:

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

System kompilacji ma informacje o symboli preprocesora reprezentujący platform docelowych objętego [obsługiwane target framework w wersji](#supported-target-framework-versions) tabeli. W przypadku używania symbolu, który reprezentuje .NET Standard i .NET Core TFM, zastępowania kropki, podkreślenia i zmienić małe litery na wielkie litery (na przykład symbol `netstandard1.4` jest `NETSTANDARD1_4`).

Pełna lista symboli preprocesora dla platform docelowych .NET Core jest:

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a>Platformy docelowe przestarzałe

Następujące struktury docelowej są przestarzałe. Pakiety przeznaczone dla tych platform docelowych należy zmigrować do wskazanego zamiany.

| Przestarzałe TFM                                                                             | Zastępczy |
| ------------------------------------------------------------------------------------------ | ----------- |
| aspnet50<br>aspnetcore50<br>dnxcore50<br>dnx<br>dnx45<br>dnx451<br>dnx452                  | Element netcoreapp  |
| polecenia DotNet<br>dotnet50<br>dotnet51<br>dotnet52<br>dotnet53<br>dotnet54<br>dotnet55<br>dotnet56 | netstandard |
| netcore50                                                                                  | uap10.0     |
| Wygraj                                                                                        | netcore45   |
| win8                                                                                       | netcore45   |
| win81                                                                                      | netcore451  |
| Windows 10                                                                                      | uap10.0     |
| winrt                                                                                      | netcore45   |

## <a name="see-also"></a>Zobacz także

- [Pakiety, metapakiety i struktury](../core/packages.md)  
- [Tworzenie bibliotek za pomocą narzędzi międzyplatformowych](../core/tutorials/libraries.md)  
- [.NET Standard](net-standard.md)  
- [Przechowywanie wersji programu .NET core](../core/versions/index.md)  
- [repozytorium GitHub DotNet/standard](https://github.com/dotnet/standard)  
- [Repozytorium GitHub narzędzia NuGet](https://github.com/joelverhagen/NuGetTools)  
- [Profile Framework na platformie .NET](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html)
