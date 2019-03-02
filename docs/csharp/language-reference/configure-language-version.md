---
title: Wybierz C# wersji językowej - C# przewodnik
description: Konfigurowanie kompilatora przeprowadzić weryfikacji składni przy użyciu określonej wersji kompilatora
ms.date: 02/28/2019
ms.openlocfilehash: 6d31a757171bd2eecdcc1fbd3da765dcb3fe45c0
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212030"
---
# <a name="select-the-c-language-version"></a>Wybierz C# wersja językowa

C# Kompilator określa domyślną wersję języka na podstawie platformy docelowej projektu lub struktury. Jeśli projekt jest przeznaczony dla framework w wersji zapoznawczej, która jest odpowiednia wersja językowa (wersja zapoznawcza), wersja językowa, używana jest wersja językowa (wersja zapoznawcza). Gdy projekt nie jest kierowana framework w wersji zapoznawczej, wersji językowej, używana jest najnowsza wersja pomocnicza.

Na przykład w okresie wersji zapoznawczej dla platformy .NET Core 3.0, każdy projekt przeznaczonego `netcoreapp3.0` lub `netstandard2.1` (zarówno w wersji zapoznawczej) użyje C# 8.0 language (również w wersji zapoznawczej). Projekty przeznaczone dla dowolnej wersji wydanej użyje C# 7.3 (Najnowsza wersja wydana wersja). To zachowanie oznacza, że jakiegokolwiek projektu, przeznaczonych dla platformy .NET Framework będzie używać najnowszej (C# 7.3). 

Ta funkcja oddziela decyzję, aby zainstalować nowe wersje zestawu SDK i narzędzi w środowisku programistycznym z decyzji, aby wprowadzić nowe funkcje języka w projekcie. Na komputerze kompilacji, można zainstalować najnowszy zestaw SDK oraz narzędzia. Każdy projekt można skonfigurować do użytku z określoną wersją języka jego kompilacji. Domyślne zachowanie oznacza, że wszelkie funkcji języka, które polegają na nowe typy lub nowe zachowanie środowiska CLR są włączone tylko wtedy, gdy projekty ukierunkowane na tych środowisk.

Zachowanie domyślne można przesłonić, określając w wersji językowej. Istnieje kilka sposobów, aby ustawić wersję językową:

- Zaufaj [szybkie działanie programu Visual Studio](#visual-studio-quick-action).
- Ustawianie wersji języka [interfejsie użytkownika Visual Studio](#set-the-language-version-in-visual-studio).
- Ręcznie Edytuj swoje [ **.csproj** pliku](#edit-the-csproj-file).
- Ustawianie wersji języka [dla wielu projektów w podkatalogu](#configure-multiple-projects).
- Konfigurowanie [ `-langversion` — opcja kompilatora](#set-the-langversion-compiler-option).

## <a name="visual-studio-quick-action"></a>Visual Studio szybkich działań.

Program Visual Studio ułatwia określenie wersji językowej, których potrzebujesz. Jeśli używasz funkcji języka, który nie jest dostępna dla wersji aktualnie skonfigurowane, Visual Studio Pokazuje potencjalne poprawki, aby zaktualizować wersję języka dla projektu.

## <a name="set-the-language-version-in-visual-studio"></a>Ustawianie wersji języka w programie Visual Studio

Można ustawić wersji w programie Visual Studio. Kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierz **właściwości**. Wybierz **kompilacji** kartę, a następnie wybierz pozycję **zaawansowane** przycisku. Z listy rozwijanej wybierz wersję. Na poniższej ilustracji przedstawiono ustawienia "najnowsza":

![Zrzut ekranu przedstawiający ustawienia zaawansowane kompilacji, w którym można określić wersji językowej](./media/configure-language-version/advanced-build-settings.png)

> [!NOTE]
> Jeśli używasz środowiska IDE programu Visual Studio do aktualizacji plików csproj, IDE tworzy osobne węzły dla każdej konfiguracji kompilacji. Będzie zazwyczaj wartość taka sama we wszystkich konfiguracjach kompilacji, ale musisz ustawiony w sposób jawny dla każdej konfiguracji kompilacji, lub wybierz pozycję "Wszystkie konfiguracje" po zmodyfikowaniu tego ustawienia. W pliku csproj, zostanie wyświetlone następujące czynności:
>
>```xml
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
>  <LangVersion>latest</LangVersion>
></PropertyGroup>
>
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
>  <LangVersion>latest</LangVersion>
> </PropertyGroup>
> ```
>

## <a name="edit-the-csproj-file"></a>Edytuj plik csproj

Wersja językowa można ustawić w swojej **.csproj** pliku. Dodawanie elementu, jak pokazano poniżej:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Wartość `latest` korzysta z najnowszą wersją pomocniczą C# języka. Prawidłowe wartości to:

|Wartość|Znaczenie|
|------------|-------------|
|wersja zapoznawcza|Kompilator akceptuje wszystkie składni języka prawidłowy z najnowszej wersji zapoznawczej.|
|najnowsza|Kompilator akceptuje składni z najnowszej wersji, kompilator (w tym wersja pomocnicza).|
|latestMajor|Kompilator akceptuje składnię najnowszej głównej wersji kompilatora.|
|8.0|Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 8.0 lub niższą.|
|7.3|Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 7.3 lub niższy.|
|7.2|Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 7.2 lub niższy.|
|7.1|Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 7.1 lub niższą.|
|7|Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 7.0 lub niższą.|
|6|Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 6.0 lub niższą.|
|5|Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 5.0 lub niższą.|
|4|Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 4.0 lub niższą.|
|3|Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 3.0 lub niższą.|
|ISO-2|Kompilator akceptuje tylko w przypadku składni, która znajduje się w 23270:2006 ISO/IEC C# (2.0) |
|ISO-1|Kompilator akceptuje tylko w przypadku składni, która znajduje się w 23270:2003 ISO/IEC C# (1.0/1.2) |

## <a name="configure-multiple-projects"></a>Konfigurowanie wielu projektów

Możesz utworzyć **Directory.build.props** pliku, który zawiera `<LangVersion>` element, aby skonfigurować wiele katalogów. Należy zwykle to zrobić w katalogu rozwiązania. Dodaj następujące polecenie, aby **Directory.build.props** pliku w katalogu rozwiązania:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

Teraz kompilacje w każdym podkatalogu katalogu zawierającego ten plik będzie używać C# składni w wersji 7.3. Aby uzyskać więcej informacji, zobacz artykuł [Dostosowywanie kompilacji](/visualstudio/msbuild/customize-your-build).

## <a name="set-the-langversion-compiler-option"></a>Ustaw langversion — opcja kompilatora

Możesz użyć `-langversion` opcji wiersza polecenia. Aby uzyskać więcej informacji, zobacz artykuł [- langversion](../language-reference/compiler-options/langversion-compiler-option.md) — opcja kompilatora. Możesz wyświetlić listę prawidłowych wartości, wpisując `csc -langversion:?`.
