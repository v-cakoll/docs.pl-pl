---
title: -pathmap (opcje kompilatora C#)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 36196ffea19cfde7ff5f830ea358d2bd83edf419
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472850"
---
# <a name="-pathmap-c-compiler-options"></a>-pathmap (opcje kompilatora C#)

**- Pathmap** — opcja kompilatora określa sposób mapowania ścieżek fizycznych źródła ścieżkę nazwy w danych wyjściowych przez kompilator.

## <a name="syntax"></a>Składnia

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a>Argumenty

 `path1` Pełna ścieżka do plików źródłowych w bieżącym środowisku

 `sourcePath1` Ścieżka źródłowa podstawić `path1` w żadnych plików wyjściowych.

Aby określić wiele ścieżek zamapowanych źródła, rozdzielić przecinkami.

## <a name="remarks"></a>Uwagi

Kompilator zapisuje ścieżki źródłowej ścieżki do jego dane wyjściowe z następujących powodów:

1. Argument ścieżki źródłowej zostanie zastąpiony podczas <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> jest stosowany do parametr opcjonalny.
1. Ścieżka źródłowa jest osadzony w pliku PDB.
1. Ścieżka pliku PDB jest osadzony w pliku PE (przenośny plik wykonywalny).

Ta opcja mapuje każdej ścieżki fizycznej na komputerze, na którym jest uruchomiona przez kompilator do odpowiedniego ścieżki, w której mają być zapisywane w plikach wyjściowych.

## <a name="example"></a>Przykład

Kompiluj `t.cs` w katalogu **C:\\pracy\\testy** i mapowanie katalogowi na potrzeby **\publish** w danych wyjściowych:

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a>Zobacz także

 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
