---
title: -recurse (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a053e5676b10de3bd2eecf6de8be7a30329962af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="recurse-c-compiler-options"></a>/recurse (opcje kompilatora C#)
Opcja/recurse umożliwia skompilować plików kodu źródłowego we wszystkich katalogach podrzędnych albo określonego katalogu (dir) lub w katalogu projektu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Argumenty  
 `dir`(opcjonalnie)  
 Katalog, w którym ma rozpocząć wyszukiwanie. Jeśli nie zostanie określony, wyszukiwanie rozpoczyna się w katalogu projektu.  
  
 `file`  
 Pliki do wyszukania. Symbole wieloznaczne są dozwolone.  
  
## <a name="remarks"></a>Uwagi  
 **/Recurse** opcja umożliwia skompilować plików kodu źródłowego we wszystkich katalogach podrzędnych określonego katalogu (`dir`) lub w katalogu projektu.  
  
 Symbole wieloznaczne w nazwie pliku służy do Kompiluj wszystkie zgodne pliki w katalogu projektu bez użycia **/recurse**.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Kompiluje wszystkie pliki C# w bieżącym katalogu:  
  
```console  
csc *.cs  
```  
  
 Kompiluje wszystkie pliki C# w katalogu dir1\dir2 i wszystkie jego katalogów i generuje dir2.dll:  
  
```console  
csc /target:library /out:dir2.dll /recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
