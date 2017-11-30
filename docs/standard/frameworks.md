---
title: Docelowych platform
description: "Więcej informacji na temat platformy docelowej dla aplikacji .NET Core i bibliotek."
author: richlander
ms.author: mairaw
ms.date: 09/22/2017
ms.topic: article
ms.custom: updateeachrelease
ms.prod: .net
ms.technology: dotnet-standard
ms.openlocfilehash: 20152a951f11b1b923209b56b31663a9a8a81587
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="target-frameworks"></a>Docelowych platform

Target framework aplikacji lub w bibliotece, określasz zestaw interfejsów API, który ma być dostępna dla aplikacji lub biblioteki. Platforma docelowa określa się w pliku projektu przy użyciu docelowego Framework monikerów (TFMs).

To aplikacja lub biblioteki można wersja docelowa platformy [.NET Standard](~/docs/standard/net-standard.md). Wersje .NET standard reprezentują zestawy standardowych interfejsów API we wszystkich wdrożeniach .NET. Na przykład biblioteki można docelowa platformy .NET Standard w wersji 1.6 i uzyskanie dostępu do interfejsów API tej funkcji w .NET Core i .NET Framework za pomocą tej samej bazy kodu.

Aplikacja lub biblioteka też określić konkretnej implementacji .NET, aby uzyskać dostęp do konkretnej implementacji interfejsów API. Na przykład aplikację, która jest przeznaczony dla platformy Xamarin.iOS (na przykład `Xamarin.iOS10`) uzyskuje dostęp do otoki dostarczane do platformy Xamarin iOS interfejsu API dla systemu iOS 10 lub aplikacji, przeznaczonego dla platformy uniwersalnej systemu Windows (UWP, `uap10.0`) ma dostęp do interfejsów API, które kompilacji dla urządzeń z systemem Windows 10.

Dla niektórych platform docelowych (na przykład, .NET Framework) interfejsy API są definiowane przez zestawy, że platformę instaluje na komputerze i mogą obejmować struktury aplikacji interfejsów API (na przykład ASP.NET).

Dla struktury docelowej na podstawie pakietu (na przykład standardowe .NET i .NET Core) interfejsy API są definiowane przez pakiety zawartych w aplikacji lub biblioteki. A *metapackage* jest pakietem NuGet, który nie ma zawartości z oddzielnie, ale znajduje się wykaz zależności (inne pakiety). Platformy docelowej na podstawie pakietu NuGet określa niejawnie metapackage, który odwołuje się do wszystkich pakietów, które składają się platformę.

## <a name="latest-target-framework-versions"></a>Najnowsze target framework w wersji

W poniższej tabeli opisano najbardziej typowe docelowych platform, jak w przypadku odwołania i wersję [.NET Standard](~/docs/standard/net-standard.md) ich wdrożenia. Te target framework w wersji są najnowsze wersje stabilna. Wersje wstępne nie są wyświetlane. Docelowy Framework Moniker (TFM) jest standardowym formacie token służący do określania platformę docelową aplikacji .NET lub biblioteki. 

| Platforma docelowa      | Najnowsza wersja | Moniker platformy docelowej (TFM) | Zaimplementowany <br/> .NET w wersji standard |
| :-------------------: | :------------: | :----------------------------: | :-------------------------------------: |
| .NET standard         | 2.0            | netstandard2.0                 | Brak                                     |
| Aplikacja programu .NET core | 2.0            | netcoreapp2.0                  | 2.0                                     |
| .NET Framework        | 4.7.1          | net471                         | 2.0                                     |

## <a name="supported-target-framework-versions"></a>Obsługiwane target framework w wersji

Platforma docelowa jest zwykle przywoływany przez TFM. W poniższej tabeli przedstawiono docelowych platform obsługiwanych przez zestaw SDK .NET Core i klienta NuGet. Odpowiedniki są wyświetlane w nawiasach kwadratowych. Na przykład `win81` jest równoważne TFM do `netcore451`.

| Platforma docelowa           | TFM |
| -------------------------- | --- |
| .NET standard              | netstandard1.0<br>netstandard1.1<br>netstandard1.2<br>netstandard1.3<br>netstandard1.4<br>netstandard1.5<br>netstandard1.6<br>netstandard2.0 |
| .NET Core                  | netcoreapp1.0<br>netcoreapp1.1<br>netcoreapp2.0 |
| .NET Framework             | net11<br>net20<br>Net35<br>net40<br>net403<br>net45<br>net451<br>net452<br>net46<br>net461<br>net462<br>net47<br>net471 |
| Sklep Windows              | netcore [netcore45]<br>netcore45 [win] [win8]<br>netcore451 [win81] |
| .NET micro Framework       | netmf |
| Silverlight                | sl4<br>sl5 |
| Windows Phone              | WP [wp7]<br>wp7<br>wp75<br>wp8<br>wp81<br>wpa81 |
| Platforma uniwersalna systemu Windows | uap [uap10.0]<br>uap10.0 [win10] [netcore50] |

## <a name="how-to-specify-target-frameworks"></a>Sposób określania docelowych platform

W pliku projektu określono struktur docelowych. Gdy framework pojedynczym elementem docelowym jest określony, użyj **TargetFramework** elementu. Następujący plik projekt aplikacji konsoli Pokazuje, jak pod kątem .NET Core 2.0:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Podczas określania wielu platform docelowych może odwoływać się na nim warunkowo zestawy dla każdej platformy docelowej. W kodzie, będzie można warunkowo kompilować względem tych zestawów przy użyciu symboli preprocesora z *if to inaczej* logiki.

Następujący plik projektu biblioteki jest przeznaczony dla interfejsów API programu .NET Standard (`netstandard1.4`) i interfejsów API programu .NET Framework (`net40` i `net45`). Użyj liczbę mnogą **TargetFrameworks** element z wielu platform docelowych. Uwaga jak `Condition` atrybuty obejmują pakietów konkretnej implementacji podczas kompilowania biblioteki dla dwóch TFMs Framework .NET:

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

W bibliotece lub aplikacji należy napisać kod warunkowego kompilacji dla każdej platformy docelowej:

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

System kompilacji zna symboli preprocesora reprezentujący docelowych platform pokazano [obsługiwane target framework w wersji](#supported-target-framework-versions) tabeli. Używając symbol, który reprezentuje .NET Standard lub .NET Core TFM zastępowania znaków kropki, podkreślenia i zmień małych liter na wielkie litery (na przykład symbol `netstandard1.4` jest `NETSTANDARD1_4`).

Pełna lista symboli preprocesora dla struktury docelowej platformy .NET Core jest:

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a>Przestarzałe docelowych platform

Następujące struktury docelowej są przestarzałe. Pakietów przeznaczonych dla tych platform docelowych należy zmigrować do wskazanej zastępcze.

| Przestarzałe TFM                                                                             | Zastąpienie |
| ------------------------------------------------------------------------------------------ | ----------- |
| aspnet50<br>aspnetcore50<br>dnxcore50<br>DNX<br>dnx45<br>dnx451<br>dnx452                  | netcoreapp  |
| DotNet<br>dotnet50<br>dotnet51<br>dotnet52<br>dotnet53<br>dotnet54<br>dotnet55<br>dotnet56 | krótkich nazw netstandard |
| netcore50                                                                                  | uap10.0     |
| win                                                                                        | netcore45   |
| Windows 8                                                                                       | netcore45   |
| win81                                                                                      | netcore451  |
| Windows 10                                                                                      | uap10.0     |
| winrt                                                                                      | netcore45   |

## <a name="see-also"></a>Zobacz także

[Pakiety, Metapackages i platform](~/docs/core/packages.md)  
[Tworzenie bibliotek z wielu narzędzi platformy](~/docs/core/tutorials/libraries.md)  
[.NET standard](~/docs/standard/net-standard.md)  
[Przechowywanie wersji programu .NET core](~/docs/core/versions/index.md)  
[repozytorium GitHub DotNet/standard](https://github.com/dotnet/standard)  
[Repozytorium GitHub narzędzia NuGet](https://github.com/joelverhagen/NuGetTools)  
[Profile Framework w .NET](http://blog.stephencleary.com/2012/05/framework-profiles-in-net.html)
