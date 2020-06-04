---
title: -subsystemversion
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
ms.openlocfilehash: 09ddc4bb735b645e09d34198c66dff78183592bf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403086"
---
# <a name="-subsystemversion-visual-basic"></a>-subsystemversion (Visual Basic)

Określa minimalną wersję podsystemu, w którym można uruchomić wygenerowany plik wykonywalny, a tym samym określa wersje systemu Windows, w których można uruchomić plik wykonywalny. Najczęściej ta opcja zapewnia, że plik wykonywalny może korzystać z określonych funkcji zabezpieczeń, które nie są dostępne w starszych wersjach systemu Windows.

> [!NOTE]
> Aby określić podsystem, użyj opcji kompilatora [-Target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) .

## <a name="syntax"></a>Składnia

```vb
-subsystemversion:major.minor
```

## <a name="parameters"></a>Parametry

`major.minor`

Minimalna wymagana wersja podsystemu, wyrażona w notacji kropkowej dla wersji głównych i pomocniczych. Można na przykład określić, że aplikacja nie może działać w systemie operacyjnym starszym niż Windows 7, jeśli wartość tej opcji zostanie ustawiona na 6,01, jak w dalszej części tego tematu. Należy określić wartości dla `major` i `minor` jako liczby całkowite.

Zera wiodące w `minor` wersji nie zmieniają wersji, ale końcowe zera to. Na przykład 6,1 i 6,01 odnoszą się do tej samej wersji, ale 6,10 odwołuje się do innej wersji. Zalecamy wyrażenie wersji pomocniczej jako dwóch cyfr, aby uniknąć pomyłek.

## <a name="remarks"></a>Uwagi

W poniższej tabeli wymieniono typowe wersje podsystemów systemu Windows.

|Wersja systemu Windows|Wersja podsystemu|
|---------------------|-----------------------|
|Windows 2000|5,00|
|Windows XP|5,01|
|Windows Server 2003|5,02|
|Windows Vista|6,00|
|Windows 7|6,01|
|Windows Server 2008|6,01|
|Windows 8|6,02|

## <a name="default-values"></a>Wartości domyślne

Wartość domyślna opcji kompilatora **-subsystemversion** zależy od warunków z poniższej listy:

- Wartość domyślna to 6,02, jeśli ustawiona jest jakakolwiek opcja kompilatora na poniższej liście:

  - [-target:appcontainerexe](target.md)

  - [-target:winmdobj](target.md)

  - [-Platforma: ARM](platform.md)

- Wartość domyślna to 6,00, jeśli używasz programu MSBuild, jesteś celem .NET Framework 4,5 i nie ustawisz żadnych opcji kompilatora określonych wcześniej na tej liście.

- Wartość domyślna to 4,00, jeśli żaden z poprzednich warunków nie ma wartości true.

## <a name="setting-this-option"></a>Ustawienie tej opcji

Aby ustawić opcję kompilatora **-subsystemversion** w programie Visual Studio, należy otworzyć plik. vbproj i określić wartość `SubsystemVersion` właściwości w kodzie XML programu MSBuild. Nie można ustawić tej opcji w środowisku IDE programu Visual Studio. Aby uzyskać więcej informacji, zobacz "wartości domyślne" wcześniej w tym temacie lub [wspólnych właściwościach projektu MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](index.md)

- [Właściwości programu MSBuild](/visualstudio/msbuild/msbuild-properties)
