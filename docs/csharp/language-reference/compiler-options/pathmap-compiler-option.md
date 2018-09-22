---
title: -elemencie pathmap (opcje kompilatora C#)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 277ab8e094f28fd5e3cbba4de12e742bb9614730
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581957"
---
# <a name="-pathmap-c-compiler-options"></a>-elemencie pathmap (opcje kompilatora C#)

**- Elemencie pathmap** — opcja kompilatora określa sposób mapowania ścieżek fizycznych na dane wyjściowe nazwy ścieżki źródłowej przez kompilator.

## <a name="syntax"></a>Składnia

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a>Argumenty

 `path1` Pełna ścieżka do plików źródłowych w bieżącym środowisku

 `sourcePath1` Ścieżka źródłowa zamieniony na `path1` w żadnych plików wyjściowych.

Aby określić wiele ścieżek zamapowanego źródła, rozdzielić przecinkami.

## <a name="remarks"></a>Uwagi

Kompilator zapisuje ścieżki źródłowej w ścieżce do jego dane wyjściowe z następujących powodów:

1. Ścieżka źródłowa zostanie zastąpiony argument podczas <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> jest stosowany do opcjonalnego parametru.
1. Ścieżka źródłowa jest osadzony w pliku PDB.
1. Ścieżka do pliku PDB jest osadzony w pliku PE (przenośny plik wykonywalny).

Ta opcja mapuje każdej ścieżki fizycznej na komputerze, na którym jest uruchamiany kompilator do odpowiedniej ścieżki, w której powinny być zapisywane w plikach wyjściowych.

## <a name="example"></a>Przykład

Skompilować `t.cs` w katalogu **C:\\pracy\\testy** i zamapuj katalogowi na potrzeby **\publish** w danych wyjściowych:

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
