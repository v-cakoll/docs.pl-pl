---
title: Platformy docelowe w projektach w stylu SDK — .NET
description: Dowiedz się więcej o platformach docelowych dla aplikacji i bibliotek .NET Core.
ms.date: 12/03/2019
ms.custom: updateeachrelease
ms.technology: dotnet-standard
ms.openlocfilehash: 33beb5606cbf857cc41b739f256482b0298f1fb1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400555"
---
# <a name="target-frameworks-in-sdk-style-projects"></a>Platformy docelowe w projektach w stylu SDK

Podczas kierowania struktury w aplikacji lub bibliotece, określasz zestaw interfejsów API, które chcesz udostępnić w aplikacji lub bibliotece. Należy określić platformę docelową w pliku projektu przy użyciu target framework monikers (TFM).

Aplikacja lub biblioteka może kierować na wersję [programu .NET Standard](net-standard.md). Wersje standardu .NET reprezentują znormalizowane zestawy interfejsów API we wszystkich implementacjach .NET. Na przykład biblioteka może kierować .NET Standard 1.6 i uzyskać dostęp do interfejsów API, które działają w programie .NET Core i .NET Framework przy użyciu tej samej bazy kodu.

Aplikacja lub biblioteka może również kierować określoną implementację .NET, aby uzyskać dostęp do interfejsów API specyficznych dla implementacji. Na przykład aplikacja przeznaczona dla systemu Xamarin.iOS (na `Xamarin.iOS10`przykład) uzyskuje dostęp do otoki interfejsu API systemu IOS dostarczonego przez platformę `uap10.0`IOS dla systemu iOS 10 lub aplikacji przeznaczonej dla platformy uniwersalnej systemu Windows (UWP) ma dostęp do interfejsów API kompilowanych dla urządzeń z systemem Windows 10.

W przypadku niektórych platform docelowych (na przykład .NET Framework) interfejsy API są definiowane przez zestawy, które struktura instaluje w systemie i mogą obejmować interfejsy API platformy aplikacji (na przykład ASP.NET).

W przypadku platform docelowych opartych na pakietach (na przykład .NET Standard i .NET Core) interfejsy API są definiowane przez pakiety zawarte w aplikacji lub bibliotece. *Metapakiet* jest pakietEm NuGet, który nie ma własnej zawartości, ale jest listą zależności (innych pakietów). Platforma docelowa oparta na pakiecie NuGet niejawnie określa metapakiet, który odwołuje się do wszystkich pakietów, które razem tworzą strukturę.

## <a name="latest-target-framework-versions"></a>Najnowsze wersje struktury docelowej

W poniższej tabeli zdefiniowano najbardziej typowe platformy docelowe, jak się do nich odwołuje i którą wersję [standardu .NET,](net-standard.md) którą implementują. Te wersje platformy docelowej są najnowsze wersje stabilne. Wersje wstępne nie są wyświetlane. Target Framework Moniker (TFM) jest znormalizowany format tokenu do określania struktury docelowej aplikacji lub biblioteki .NET.

| Struktura docelowa      | Najnowsza <br/> Stabilna wersja | Domina platformy docelowej (TFM) | Zaimplementowana <br/> Wersja standardowa .NET |
| :-------------------: | :-------------------------: | :----------------------------: | :-------------------------------------: |
| .NET Standard         | 2.1                         | standard netto2,1                 | Nie dotyczy                                     |
| .NET Core             | 3.1                         | netcoreapp3,1                  | 2.1                                     |
| .NET Framework        | 4.8                         | netto48                          | 2.0                                     |

## <a name="supported-target-framework-versions"></a>Obsługiwane wersje struktury docelowej

Platforma docelowa jest zazwyczaj odwołuje się do TFM. W poniższej tabeli przedstawiono struktury docelowe obsługiwane przez zestaw SDK .NET Core i klienta NuGet. Odpowiedniki są wyświetlane w nawiasach. Na przykład `win81` jest odpowiednikiem `netcore451`TFM do .

| Struktura docelowa           | Tfm |
| -------------------------- | --- |
| .NET Standard              | standard netto1,0<br>standard netto1,1<br>standard netto1,2<br>standard netto1,3<br>standard netto1,4<br>standard netto1,5<br>standard netto1,6<br>standard netto2,0<br>standard netto2,1 |
| .NET Core                  | netcoreapp1.0<br>netcoreapp1.1<br>netcoreapp2.0<br>netcoreapp2.1<br>netcoreapp2,2<br>netcoreapp3.0<br>netcoreapp3,1 |
| .NET Framework             | netto11<br>netto20<br>netto35<br>netto40<br>netto403<br>netto45<br>netto451<br>netto452<br>netto46<br>net461<br>netto462<br>netto47<br>netto471<br>netto472<br>netto48 |
| Windows Store              | netcore [netcore45]<br>netcore45 [wygrana] [win8]<br>netcore451 [win81] |
| Platforma .NET Micro Framework       | netmf ( netmf ) |
| Silverlight                | sl4<br>sl5 |
| Windows Phone              | wp [wp7]<br>wp7<br>wp75<br>wp8<br>wp81<br>wpa81 |
| Platforma uniwersalna systemu Windows | uap [uap10.0]<br>uap10.0 [win10] [netcore50] |

## <a name="how-to-specify-target-frameworks"></a>Jak określić ramy docelowe

Platformy docelowe są określone w pliku projektu. Po określeniu pojedynczej platformy docelowej należy użyć **elementu TargetFramework.** Następujący plik projektu aplikacji konsoli pokazuje, jak kierować.NET Core 3.0:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Po określeniu wielu platform docelowych, można warunkowo odwoływać się do zestawów dla każdej platformy docelowej. W kodzie można warunkowo skompilować względem tych zestawów przy użyciu symboli preprocesora z logiką *if-then-else.*

Następujący plik projektu biblioteki jest przeznaczony dla`netstandard1.4`interfejsów API standardu`net40` .NET ( ) i interfejsów API programu .NET Framework ( i `net45`). Użyj elementu **TargetFrameworks** w liczbie mnogiej z wieloma platformami docelowymi. Należy zauważyć, `Condition` jak atrybuty obejmują pakiety specyficzne dla implementacji, gdy biblioteka jest kompilowana dla dwóch tfmów .NET Framework:

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

W bibliotece lub aplikacji piszesz kod warunkowy do kompilacji dla każdej struktury docelowej:

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

System kompilacji jest świadomy symboli preprocesora reprezentujących platformdocelowych pokazano w [obsługiwane wersje struktury docelowej](#supported-target-framework-versions) tabeli, gdy używasz projektów w stylu SDK. W przypadku używania symbolu reprezentującego standard .NET lub .NET Core TFM, zamień kropkę na znak podkreślenia i zmień małe litery na wielkie litery (na przykład symbolem jest `netstandard1.4` `NETSTANDARD1_4`).

Pełna lista symboli preprocesora dla platform docelowych .NET Core jest:

[!INCLUDE [Preprocessor symbols](../../includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a>Przestarzałe struktury docelowe

Następujące struktury docelowe są przestarzałe. Pakiety przeznaczone dla tych platform docelowych powinny zostać poddane migracji do wskazanych zamienników.

| Przestarzałe TFM                                                                             | Funkcja zastępująca |
| ------------------------------------------------------------------------------------------ | ----------- |
| aspnet50<br>aspnetcore50<br>dnxcore50<br>Dnx<br>dnx45<br>dnx451<br>dnx452                  | netcoreapp ( netcoreapp )  |
| dotnet<br>dotnet50<br>dotnet51<br>dotnet52<br>dotnet53<br>dotnet54<br>dotnet55<br>dotnet56 | standard netto |
| netcore50                                                                                  | Uap10.0     |
| Wygrać                                                                                        | netcore45   |
| win8                                                                                       | netcore45   |
| win81                                                                                      | netcore451  |
| win10                                                                                      | Uap10.0     |
| Winrt                                                                                      | netcore45   |

## <a name="see-also"></a>Zobacz też

- [Pakiety, metapakiety i struktury](../core/packages.md)
- [Tworzenie bibliotek za pomocą narzędzi międzyplatformowych](../core/tutorials/libraries.md)
- [.NET Standard](net-standard.md)
- [Przechowywanie wersji rdzenia .NET](../core/versions/index.md)
- [dotnet/standardowe repozytorium GitHub](https://github.com/dotnet/standard)
- [Repozytorium NuGet Tools GitHub](https://github.com/joelverhagen/NuGetTools)
- [Profile struktury w .NET](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html)
