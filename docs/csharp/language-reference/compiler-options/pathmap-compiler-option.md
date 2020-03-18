---
title: -pathmap (Opcje kompilatora C#)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 48e96d2ec2ccbea83d573c0eb3630b1591c407a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606628"
---
# <a name="-pathmap-c-compiler-options"></a>-pathmap (Opcje kompilatora C#)

Opcja kompilatora **-pathmap** określa sposób mapowania ścieżek fizycznych na nazwy ścieżek źródłowych wyprowadzanych przez kompilator.

## <a name="syntax"></a>Składnia

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a>Argumenty

 `path1`Pełna ścieżka do plików źródłowych w bieżącym środowisku

 `sourcePath1`Ścieżka źródłowa `path1` zastąpiona w dowolnych plikach wyjściowych.

Aby określić wiele mapowanych ścieżek źródłowych, należy oddzielić każdy z przecinkiem.

## <a name="remarks"></a>Uwagi

Kompilator zapisuje ścieżkę źródłową w danych wyjściowych z następujących powodów:

1. Ścieżka źródłowa jest zastępowana <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> argumentem, gdy jest stosowany do parametru opcjonalnego.
1. Ścieżka źródłowa jest osadzona w pliku PDB.
1. Ścieżka pliku PDB jest osadzona w pliku PE (przenośny plik wykonywalny).

Ta opcja mapuje każdą ścieżkę fizyczną na komputerze, na którym kompilator jest uruchamiany na odpowiednią ścieżkę, która powinna być zapisana w plikach wyjściowych.

## <a name="example"></a>Przykład

Skompiluj `t.cs` w katalogu **C:\\testy\\robocze** i mapuj ten katalog do **\publish** w danych wyjściowych:

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
