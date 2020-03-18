---
title: alias extern — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 86202333484933d7449b0c4d8c5a3f1a63cd7775
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713544"
---
# <a name="extern-alias-c-reference"></a>extern alias (odwołanie w C#)
Może być wymagane odwołanie się do dwóch wersji zestawów, które mają te same nazwy typów w pełni kwalifikowane. Na przykład może być trzeba użyć dwóch lub więcej wersji zestawu w tej samej aplikacji. Za pomocą aliasu zewnętrznego zestawu przestrzenie nazw z każdego zestawu mogą być opakowane wewnątrz obszarów nazw na poziomie głównym nazwanych aliasem, co umożliwia ich użycie w tym samym pliku.  
  
> [!NOTE]
> [Extern](./extern.md) słowo kluczowe jest również używany jako modyfikator metody, deklarując metodę zapisaną w kodzie niezarządzanym.  
  
 Aby odwołać się do dwóch zestawów o tych samych w pełni kwalifikowanych nazwach typów, alias musi być określony w wierszu polecenia w następujący sposób:  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Spowoduje to utworzenie aliasów `GridV1` zewnętrznych i `GridV2`. Aby używać tych aliasów z poziomu programu, `extern` należy odwoływać się do nich za pomocą słowa kluczowego. Przykład:  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Każda deklaracja aliasu extern wprowadza dodatkową obszar nazw na poziomie głównym, który paralele (ale nie znajduje się w) globalnej przestrzeni nazw. W związku z tym typy z każdego zestawu można odwoływać się bez dwuznaczności przy użyciu ich w pełni kwalifikowanej nazwy, zakorzenione w odpowiednim aliasie obszaru nazw.  
  
 W poprzednim przykładzie `GridV1::Grid` będzie kontrola siatki `grid.dll` `GridV2::Grid` z , i `grid20.dll`będzie kontrola siatki z .  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [:: Operator](../operators/namespace-alias-qualifier.md)
- [-reference (Opcje kompilatora C#)](../compiler-options/reference-compiler-option.md)
