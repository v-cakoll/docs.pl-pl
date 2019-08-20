---
title: -elemencie pathmap (C# opcje kompilatora)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 48e96d2ec2ccbea83d573c0eb3630b1591c407a9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606628"
---
# <a name="-pathmap-c-compiler-options"></a>-elemencie pathmap (C# opcje kompilatora)

Opcja kompilatora **-elemencie pathmap** określa sposób mapowania ścieżek fizycznych do nazw ścieżek źródłowych wyjściowych przez kompilator.

## <a name="syntax"></a>Składnia

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a>Argumenty

 `path1`Pełna ścieżka do plików źródłowych w bieżącym środowisku

 `sourcePath1`Ścieżka źródłowa zastępują dla `path1` plików wyjściowych.

Aby określić wiele mapowanych ścieżek źródłowych, rozdziel je przecinkami.

## <a name="remarks"></a>Uwagi

Kompilator zapisuje ścieżkę źródłową do danych wyjściowych z następujących powodów:

1. Ścieżka źródłowa jest zastępowana argumentem, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> gdy jest stosowany do opcjonalnego parametru.
1. Ścieżka źródłowa jest osadzona w pliku PDB.
1. Ścieżka pliku PDB jest osadzona w pliku PE (przenośny plik wykonywalny).

Ta opcja mapuje każdą ścieżkę fizyczną na komputerze, na którym kompilator jest uruchamiany do odpowiedniej ścieżki, która powinna być zapisywana w plikach wyjściowych.

## <a name="example"></a>Przykład

Kompiluj `t.cs` w katalogu **C:\\\\Work Tests** i Mapuj ten katalog na **\publish** w danych wyjściowych:

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
