---
title: Nie można odwołać się do elementu „<name>”, ponieważ jest to składowa pola „<name>”, którego typem jest typ wartości, z klasy „<classname>”, której klasą podstawową jest „System.MarshalByRefObject”.
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: aac190119ced74496c4dd012d200fca6d895ff28
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826772"
---
# <a name="cannot-refer-to-name-because-it-is-a-member-of-the-value-typed-field-name-of-class-classname-which-has-systemmarshalbyrefobject-as-a-base-class"></a>Nie może odwoływać się do "\<nazwa >", ponieważ jest to składowa pola "\<nazwa >" klasy\<nazwa_klasy > "mającego"System.MarshalByRefObject"klasy bazowej
`System.MarshalByRefObject` Klasa umożliwia aplikacji, które obsługują zdalny dostęp do obiektów poza granice domeny aplikacji. Typy musi dziedziczyć `MarshalByRejectObject` klasy, gdy typ jest używany poza granice domeny aplikacji. Nie można skopiować stan obiektu, ponieważ elementy członkowskie obiektu nie są użyteczne spoza domeny aplikacji, w którym zostały utworzone.  
  
 **Identyfikator błędu:** BC30310  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdzanie odwołania, aby upewnić się, że przywoływanego elementu członkowskiego jest nieprawidłowy.  
  
2.  Kwalifikuj jawnie elementu członkowskiego z `Me` — słowo kluczowe.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.MarshalByRefObject>
- [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)
