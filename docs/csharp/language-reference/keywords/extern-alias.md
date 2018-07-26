---
title: extern alias (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: a2803d09ee64af854cad352f6a158fb84bb6d410
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960591"
---
# <a name="extern-alias-c-reference"></a>extern alias (odwołanie w C#)
Może być konieczne dwie wersje zestawów, które mają takie same nazwy w pełni kwalifikowanego typu odwołania. Na przykład trzeba użyć dwóch lub więcej wersji zestawu w tej samej aplikacji. Za pomocą alias zestawu zewnętrznego, przestrzenie nazw z każdego zestawu, może zostać zawinięty wewnątrz przestrzeni nazw poziomie głównym o nazwie określonej przez alias, który umożliwia im ma być używany w tym samym pliku.  
  
> [!NOTE]
>  [Extern](../../../csharp/language-reference/keywords/extern.md) — słowo kluczowe jest również używane jako modyfikator metody, deklarowania metody zapisaną w kodzie niezarządzanym.  
  
 Aby odwołać się dwa zestawy za pomocą tych samych nazw w pełni kwalifikowanego typu, alias musi być określona w wierszu polecenia w następujący sposób:  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Spowoduje to utworzenie aliasów zewnętrznych `GridV1` i `GridV2`. Aby użyć te aliasy z poziomu używanego programu, odwoływać się do nich za pomocą `extern` — słowo kluczowe. Na przykład:  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Każdy extern Deklaracja aliasu wprowadza dodatkowe obszar nazw w katalogu głównego, który równoleżnikami (ale nie leży w obrębie) globalnej przestrzeni nazw. Ten sposób typów z każdego zestawu może odnosić się bez niejednoznaczności przy użyciu w pełni kwalifikowaną nazwę, osadzonego w odpowiednich alias przestrzeni nazw.  
  
 W poprzednim przykładzie `GridV1::Grid` będzie formant siatki z `grid.dll`, i `GridV2::Grid` będzie formant siatki z `grid20.dll`.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Słowa kluczowe przestrzeni nazw](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [::, operator](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [/ Reference (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
