---
title: -recurse (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: c82e3019e1a1e3ba45a7000312b54b9d7f64a2db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606739"
---
# <a name="-recurse-c-compiler-options"></a>-recurse (Opcje kompilatora C#)
Opcja -recurse umożliwia kompilowanie plików kodu źródłowego we wszystkich katalogach podrzędnych określonego katalogu (dir) lub katalogu projektu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Argumenty  
 `dir` (opcjonalnie)  
 Katalog, w którym ma się rozpocząć wyszukiwanie. Jeśli nie zostanie to określone, wyszukiwanie rozpoczyna się w katalogu projektu.  
  
 `file`  
 Pliki do wyszukania. Znaki wieloznaczne są dozwolone.  
  
## <a name="remarks"></a>Uwagi  
 Opcja **-recurse** umożliwia kompilowanie plików kodu źródłowego we wszystkich katalogach`dir`podrzędnych określonego katalogu ( ) lub katalogu projektu.  
  
 Symboli wieloznacznych w nazwie pliku można skompilować wszystkie pasujące pliki w katalogu projektu bez użycia **-recurse**.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Kompiluje wszystkie pliki C# w bieżącym katalogu:  
  
```console  
csc *.cs  
```  
  
 Kompiluje wszystkie pliki C# w katalogu dir1\dir2 i wszystkie katalogi poniżej i generuje dir2.dll:  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
