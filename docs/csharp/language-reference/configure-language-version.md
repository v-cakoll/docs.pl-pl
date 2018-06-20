---
title: Wybierz C# wersję językową — przewodnik C#
description: Konfigurowanie kompilatora do sprawdzania poprawności składni przy użyciu wersji określonego kompilatora
ms.date: 05/24/2018
ms.openlocfilehash: 9b91e62168ced0f373e1a55def8b279dc64833d8
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208383"
---
# <a name="select-the-c-language-version"></a>Wybierz wersję języka C#

Kompilator języka C# domyślnie przyjmowana jest najnowsza wersja główna języka, który został zwolniony. Można skompilować żadnego projektu przy użyciu nowej wersji punkt języka. Wybieranie nowszej wersji języka umożliwia projektu korzystać z najnowszych funkcji języka. W innych sytuacjach konieczne może zweryfikować, czy czysto kompiluje projektu przy użyciu starszej wersji języka.

Ta funkcja zapewnia oddzielenie decyzję, aby zainstalować nowe wersje zestawu SDK i narzędzia w środowisku projektowania z decyzji, aby włączyć nowe funkcje językowe w projekcie. Najnowsze narzędzia i zestawu SDK można zainstalować na komputerze kompilacji. Każdy projekt można skonfigurować do korzystania z określonej wersji języka dla jego kompilacji.

Istnieje kilka sposobów, aby ustawić wersję językową:

- Zależne od [szybkie działanie programu Visual Studio](#visual-studio-quick-action).
- Ustaw wersję językową [interfejsu użytkownika programu Visual Studio](#set-the-language-version-in-visual-studio).
- Ręcznie Edytuj Twojej [ **.csproj** pliku](#edit-the-csproj-file).
- Ustaw wersję językową [dla wielu projektów w podkatalogu](#configure-multiple-projects).
- Skonfiguruj [ `-langversion` — opcja kompilatora](#set-the-langversion-compiler-option).

## <a name="visual-studio-quick-action"></a>Visual Studio szybkich akcji.

Visual Studio ułatwia określenie wersji językowej, które są potrzebne. Jeśli używasz funkcji języka, który nie jest dostępny dla aktualnie skonfigurowana wersja programu Visual Studio zawiera potencjalne rozwiązania można zaktualizować wersji językowej dla projektu.

## <a name="set-the-language-version-in-visual-studio"></a>Ustaw wersja językowa programu Visual Studio

Wersja można ustawić w programie Visual Studio. Kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierz **właściwości**. Wybierz **kompilacji** i wybierz **zaawansowane** przycisku. Na liście rozwijanej wybierz wersję. Na poniższej ilustracji przedstawiono ustawienie "najnowszej":

![Zrzut ekranu przedstawiający ustawienia zaawansowane kompilacji, w którym można określić wersji językowej](./media/configure-language-version/advanced-build-settings.png)

> [!NOTE]
> Jeśli używasz programu Visual Studio IDE do aktualizacji plików csproj IDE tworzy osobne węzły dla każdej konfiguracji kompilacji. Będzie zazwyczaj wartość taka sama we wszystkich konfiguracjach kompilacji, ale należy jawnie ustaw dla każdej konfiguracji kompilacji, lub wybierz opcję "Wszystkie konfiguracje" po zmodyfikowaniu tego ustawienia. W pliku csproj, pojawi się następujące:
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

Można ustawić w wersji językowej programu **.csproj** pliku. Dodaj element podobne do poniższych:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Wartość `latest` korzysta z najnowszej wersji pomocniczej języka C#. Prawidłowe wartości to:

|Wartość|Znaczenie|
|------------|-------------|
|default|Kompilator akceptuje wszystkie składni języka prawidłowe z najnowszej wersji głównych, który może obsługiwać.|
|ISO-1|Kompilator akceptuje tylko składni, który znajduje się w 23270:2003 ISO/IEC C# (1.0/1.2) |
|ISO-2|Kompilator akceptuje tylko składni, który znajduje się w 23270:2006 ISO/IEC C# (2.0) |
|3|Kompilator akceptuje tylko składnię, która jest dostępna w C# 3.0 lub niższy.|
|4|Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 4.0 lub niższy.|
|5|Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 5.0 lub niższy.|
|6|Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 6.0 lub niższy.|
|7|Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 7.0 lub niższy.|
|7.1|Kompilator akceptuje tylko składnię, która jest dostępna w C# 7.1 lub niższy.|
|7.2|Kompilator akceptuje tylko składnię, która jest dostępna w C# 7.2 lub niższy.|
|7.3|Kompilator akceptuje tylko składnię, która jest dostępna w C# 7.3 lub niższy.|
|najnowsze|Kompilator akceptuje wszystkie składni odpowiedni język, który może obsługiwać.|

Ciągi specjalne `default` i `latest` rozpoznać najnowszej głównej (C# 7.0) i pomocnicza wersji językowych (C# 7.3) odpowiednio zainstalowana na maszynie kompilacji.

## <a name="configure-multiple-projects"></a>Konfigurowanie wielu projektów

Można utworzyć **Directory.build.props** plik zawierający `<LangVersion>` element, aby skonfigurować wiele katalogów. Można zwykle to zrobić w katalogu rozwiązania. Dodaj następujący kod do **Directory.build.props** pliku w katalogu rozwiązania:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

Teraz kompilacje w każdym podkatalogu do katalogu zawierającego plik użyje wersji 7.3 składni języka C#. Aby uzyskać więcej informacji, zobacz artykuł na [Dostosowywanie kompilacji](/visualstudio/msbuild/customize-your-build).

## <a name="set-the-langversion-compiler-option"></a>Ustaw langversion — opcja kompilatora

Można użyć `-langversion` opcji wiersza polecenia. Aby uzyskać więcej informacji, zobacz artykuł na [- langversion](../language-reference/compiler-options/langversion-compiler-option.md) — opcja kompilatora. Można wyświetlić listę prawidłowych wartości, wpisując `csc -langversion:?`.
