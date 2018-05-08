---
title: Nie można wywnioskować argumentów typu na podstawie obiektu delegowanego
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: 757483f1e88276dd9db82de1c2a7e47b5c975b0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a>Nie można wywnioskować argumentów typu na podstawie obiektu delegowanego
Używa instrukcji przypisania `AddressOf` można przypisać adres ogólnego procedury delegata, ale nie dostarcza żadnych argumentów typu ogólnego procedury.  
  
 Zwykle po wywołaniu typu ogólnego, należy podać typ argumentu dla każdego parametru typu, który definiuje typ ogólny. Jeśli nie podasz żadnych argumentów typu, kompilator próbuje wnioskowanie typów, które mają być przekazane do parametrów typu. Jeśli kontekst nie zawiera wystarczających informacji dla kompilatora w celu uwzględnienia typów, generowany jest błąd.  
  
 **Identyfikator błędu:** BC36564  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Określ argumenty typu ogólnego procedurą w `AddressOf` wyrażenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [AddressOf, operator](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Procedury ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [Lista typów](../../../visual-basic/language-reference/statements/type-list.md)  
 [Metody rozszerzeń](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
