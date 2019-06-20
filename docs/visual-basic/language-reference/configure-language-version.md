---
title: Wybierz wersję języka Visual Basic
description: Skonfiguruj kompilatora przeprowadzić weryfikacji składni przy użyciu określonej wersji kompilatora.
ms.date: 05/24/2018
ms.openlocfilehash: 4768d59a37d168b2883396f1dea4d0c1a0ff4ca7
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268268"
---
# <a name="select-the-visual-basic-language-version"></a>Wybierz wersję języka Visual Basic

Domyślnie kompilator Visual Basic do najnowszej wersji głównej języka, która została zwolniona. Można skompilować jakiegokolwiek projektu, przy użyciu nowej wersji punktu języka. Wybieranie nowszą wersję języka umożliwia projekt tak, aby korzystać z najnowszych funkcji języków. W innych sytuacjach może być konieczne sprawdzenie, czy projekt skompilowany bez błędów, gdy używasz starszej wersji języka.

Ta funkcja oddziela decyzję, aby zainstalować nowe wersje zestawu SDK i narzędzi w środowisku programistycznym z decyzji, aby wprowadzić nowe funkcje języka w projekcie. Na komputerze kompilacji, można zainstalować najnowszy zestaw SDK oraz narzędzia. Każdy projekt można skonfigurować do użytku z określoną wersją języka jego kompilacji.

Istnieją trzy sposoby ustawiania wersji języka:

- Ręcznie Edytuj swoje [ **.vbproj** pliku](#edit-the-vbproj-file)
- Ustawianie wersji języka [dla wielu projektów w podkatalogu](#configure-multiple-projects)
- Konfigurowanie [ `-langversion` — opcja kompilatora](#set-the-langversion-compiler-option)

## <a name="edit-the-vbproj-file"></a>Edytowanie pliku vbproj

Wersja językowa można ustawić w swojej **.vbproj** pliku. Dodaj następujący element:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Wartość `latest` korzysta z najnowszej wersji pomocniczej języka Visual Basic. Prawidłowe wartości to:

|Wartość|Znaczenie|
|------------|-------------|
|default|Kompilator akceptuje wszystkie składni języka prawidłowy z najnowszej wersji głównej, która może obsługiwać.|
|9|Kompilator akceptuje tylko w przypadku składni, która jest zawarty w języku Visual Basic 9.0 lub niższą.|
|10|Kompilator akceptuje tylko w przypadku składni, która jest zawarty w języku Visual Basic 10.0 lub niższą.|
|11|Kompilator akceptuje tylko w przypadku składni, która jest zawarty w języku Visual Basic 11.0 lub niższą.|
|12|Kompilator akceptuje tylko w przypadku składni, która jest zawarty w Visual Basic 12.0 lub niższą.|
|14|Kompilator akceptuje tylko w przypadku składni, która jest zawarty w języku Visual Basic 14.0 lub niższą.|
|15|Kompilator akceptuje tylko w przypadku składni, która jest dostępne w ramach 15.0 programu Visual Basic lub niższą.|
|15.3|Kompilator akceptuje tylko w przypadku składni, która jest zawarty w Visual Basic 15.3 lub niższą.|
|15.5|Kompilator akceptuje tylko w przypadku składni, która jest dostępna w wersji 15.5 programu Visual Basic lub niższy.|
|15.8|Kompilator akceptuje tylko w przypadku składni, która jest zawarty w języku Visual Basic 15.8 lub niższą.|
|najnowsza|Kompilator akceptuje wszystkie składni obowiązujący język, który może obsługiwać.|

Ciągi specjalne `default` i `latest` rozwiązania do najnowszej wersji głównych i pomocniczych język zainstalowany na komputerze kompilacji, odpowiednio.

## <a name="configure-multiple-projects"></a>Konfigurowanie wielu projektów

Możesz utworzyć **Directory.build.props** pliku, który zawiera `<LangVersion>` element, aby skonfigurować wiele katalogów. Należy zwykle to zrobić w katalogu rozwiązania. Dodaj następujące polecenie, aby **Directory.build.props** pliku w katalogu rozwiązania:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>15.5</LangVersion>
 </PropertyGroup>
</Project>
```

Teraz kompilacje w każdym podkatalogu katalogu zawierającego ten plik będzie używać składni w wersji 15.5 programu Visual Basic. Aby uzyskać więcej informacji, zobacz artykuł [Dostosowywanie kompilacji](/visualstudio/msbuild/customize-your-build).

## <a name="set-the-langversion-compiler-option"></a>Ustaw langversion — opcja kompilatora

Możesz użyć `-langversion` opcji wiersza polecenia. Aby uzyskać więcej informacji, zobacz artykuł [- langversion](../reference/command-line-compiler/langversion.md) — opcja kompilatora. Możesz wyświetlić listę prawidłowych wartości, wpisując `vbc -langversion:?` .
