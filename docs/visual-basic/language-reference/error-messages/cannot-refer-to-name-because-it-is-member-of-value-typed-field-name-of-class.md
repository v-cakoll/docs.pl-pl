---
title: Nie można odwołać się do elementu „<name>”, ponieważ jest to składowa pola „<name>”, którego typem jest typ wartości, z klasy „<classname>”, której klasą podstawową jest „System.MarshalByRefObject”.
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: 78b0a3131b6e77ed257f200523ecebd4dfce3691
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316547"
---
# <a name="cannot-refer-to-name-because-it-is-a-member-of-the-value-typed-field-name-of-class-classname-which-has-systemmarshalbyrefobject-as-a-base-class"></a>Nie może odwoływać się do "\<nazwa >", ponieważ jest to składowa pola "\<nazwa >" klasy\<nazwa_klasy > "mającego"System.MarshalByRefObject"klasy bazowej
`System.MarshalByRefObject` Klasa umożliwia aplikacji, które obsługują zdalny dostęp do obiektów poza granice domeny aplikacji. Typy musi dziedziczyć `MarshalByRejectObject` klasy, gdy typ jest używany poza granice domeny aplikacji. Nie można skopiować stan obiektu, ponieważ elementy członkowskie obiektu nie są użyteczne spoza domeny aplikacji, w którym zostały utworzone.  
  
 **Identyfikator błędu:** BC30310  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Sprawdzanie odwołania, aby upewnić się, że przywoływanego elementu członkowskiego jest nieprawidłowy.  
  
2. Kwalifikuj jawnie elementu członkowskiego z `Me` — słowo kluczowe.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.MarshalByRefObject>
- [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)
