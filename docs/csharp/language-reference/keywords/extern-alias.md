---
title: alias zewnętrzny - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: d2ecd566731c3d2d472034ecb6412432af24c847
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422053"
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
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
- [:: operator](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)
- [/ Reference (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
