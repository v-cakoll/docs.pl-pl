---
title: "Nie można wywnioskować argumentów typu na podstawie obiektu delegowanego"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 57a3a24af32d9eb85a0f905aa3a73a956723b6d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a>Nie można wywnioskować argumentów typu na podstawie obiektu delegowanego
Używa instrukcji przypisania `AddressOf` można przypisać adres ogólnego procedury delegata, ale nie dostarcza żadnych argumentów typu ogólnego procedury.  
  
 Zwykle po wywołaniu typu ogólnego, należy podać typ argumentu dla każdego parametru typu, który definiuje typ ogólny. Jeśli nie podasz żadnych argumentów typu, kompilator próbuje wnioskowanie typów, które mają być przekazane do parametrów typu. Jeśli kontekst nie zawiera wystarczających informacji dla kompilatora w celu uwzględnienia typów, generowany jest błąd.  
  
 **Identyfikator błędu:** BC36564  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Określ argumenty typu ogólnego procedurą w `AddressOf` wyrażenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [AddressOf — Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Procedury ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [Lista typów](../../../visual-basic/language-reference/statements/type-list.md)  
 [Metody rozszerzenia](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
