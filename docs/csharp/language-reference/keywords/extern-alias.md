---
title: alias zewnętrzny — C# odwołanie
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 86202333484933d7449b0c4d8c5a3f1a63cd7775
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713544"
---
# <a name="extern-alias-c-reference"></a>extern alias (odwołanie w C#)
Może zajść konieczność odwołująca się do dwóch wersji zestawów, które mają te same nazwy typów w pełni kwalifikowana. Na przykład może być konieczne użycie co najmniej dwóch wersji zestawu w tej samej aplikacji. Korzystając z zewnętrznego aliasu zestawu, przestrzenie nazw z każdego zestawu mogą być opakowane w przestrzenie nazw poziomu głównego o nazwie alias, co umożliwia ich użycie w tym samym pliku.  
  
> [!NOTE]
> Słowo kluczowe [extern](./extern.md) jest również używane jako modyfikator metody, deklarując metodę zapisaną w kodzie niezarządzanym.  
  
 Aby odwoływać się do dwóch zestawów z tymi samymi w pełni kwalifikowanymi nazwami typu, alias musi być określony w wierszu polecenia w następujący sposób:  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Spowoduje to utworzenie aliasów zewnętrznych `GridV1` i `GridV2`. Aby użyć tych aliasów z poziomu programu, odwołując się do nich za pomocą słowa kluczowego `extern`. Na przykład:  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Każda deklaracja aliasu zewnętrznego wprowadza dodatkową przestrzeń nazw na poziomie głównym, która jest równoległa (ale nie znajduje się w obrębie) globalnej przestrzeni nazw. Z tego względu typy z każdego zestawu mogą być określane bez niejednoznaczności przy użyciu ich w pełni kwalifikowanej nazwy, w której znajduje się odpowiedni alias przestrzeni nazw.  
  
 W poprzednim przykładzie `GridV1::Grid` być kontrolką siatki z `grid.dll`, a `GridV2::Grid` być kontrolką siatki z `grid20.dll`.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [::, operator](../operators/namespace-alias-qualifier.md)
- [-Reference (C# opcje kompilatora)](../compiler-options/reference-compiler-option.md)
