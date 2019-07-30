---
title: alias zewnętrzny — C# odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: cfb662203216aa6ca208ceec20d55164c65163dc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626646"
---
# <a name="extern-alias-c-reference"></a>extern alias (odwołanie w C#)
Może zajść konieczność odwołująca się do dwóch wersji zestawów, które mają te same nazwy typów w pełni kwalifikowana. Na przykład może być konieczne użycie co najmniej dwóch wersji zestawu w tej samej aplikacji. Korzystając z zewnętrznego aliasu zestawu, przestrzenie nazw z każdego zestawu mogą być opakowane w przestrzenie nazw poziomu głównego o nazwie alias, co umożliwia ich użycie w tym samym pliku.  
  
> [!NOTE]
>  Słowo kluczowe [extern](../../../csharp/language-reference/keywords/extern.md) jest również używane jako modyfikator metody, deklarując metodę zapisaną w kodzie niezarządzanym.  
  
 Aby odwoływać się do dwóch zestawów z tymi samymi w pełni kwalifikowanymi nazwami typu, alias musi być określony w wierszu polecenia w następujący sposób:  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Spowoduje to utworzenie aliasów `GridV1` zewnętrznych `GridV2`i. Aby użyć tych aliasów z poziomu programu, odwołując się do `extern` nich za pomocą słowa kluczowego. Przykład:  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Każda deklaracja aliasu zewnętrznego wprowadza dodatkową przestrzeń nazw na poziomie głównym, która jest równoległa (ale nie znajduje się w obrębie) globalnej przestrzeni nazw. Z tego względu typy z każdego zestawu mogą być określane bez niejednoznaczności przy użyciu ich w pełni kwalifikowanej nazwy, w której znajduje się odpowiedni alias przestrzeni nazw.  
  
 W poprzednim przykładzie `GridV1::Grid` jest to formant siatki z `grid.dll`, `GridV2::Grid` który będzie formantem siatki z `grid20.dll`.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
- [:: operator](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [/Reference (C# opcje kompilatora)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
