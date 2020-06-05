---
title: Implements — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: 7fb43934d8c200ff29b1caf63cec830b2c6633ce
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404553"
---
# <a name="implements-statement"></a>Implements — Instrukcja
Określa jeden lub więcej interfejsów lub składowych interfejsu, które muszą zostać zaimplementowane w definicji klasy lub struktury, w której występuje.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>Części  
 `interfacename`  
 Wymagany. Interfejs, którego właściwości, procedury i zdarzenia mają być implementowane przez odpowiadające im elementy członkowskie klasy lub struktury.  
  
 `interfacemember`  
 Wymagany. Element członkowski interfejsu, który jest implementowany.  
  
## <a name="remarks"></a>Uwagi  
 Interfejs jest kolekcją prototypów reprezentujących elementy członkowskie (właściwości, procedury i zdarzenia), które są hermetyzowane w interfejsie. Interfejsy zawierają tylko deklaracje elementów członkowskich; klasy i struktury implementują te składowe. Aby uzyskać więcej informacji, zobacz [interfejsy](../../programming-guide/language-features/interfaces/index.md).  
  
 `Implements`Instrukcja musi być bezpośrednio zgodna z `Class` `Structure` instrukcją or.  
  
 Podczas implementowania interfejsu, należy zaimplementować wszystkie elementy członkowskie zadeklarowane w interfejsie. Pominięcie żadnego elementu członkowskiego jest uznawane za błąd składniowy. W celu zaimplementowania indywidualnego elementu członkowskiego należy określić słowo kluczowe [Implements](implements-clause.md) (które jest oddzielone od `Implements` instrukcji) przy deklarowaniu elementu członkowskiego w klasie lub strukturze. Aby uzyskać więcej informacji, zobacz [interfejsy](../../programming-guide/language-features/interfaces/index.md).  
  
 Klasy mogą używać [prywatnych](../modifiers/private.md) implementacji właściwości i procedur, ale te elementy członkowskie są dostępne tylko przez rzutowanie wystąpienia klasy implementującej na zmienną zadeklarowaną jako typ interfejsu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób użycia `Implements` instrukcji w celu zaimplementowania elementów członkowskich interfejsu. Definiuje interfejs o nazwie `ICustomerInfo` przy użyciu zdarzenia, właściwości i procedury. Klasa `customerInfo` implementuje wszystkie elementy członkowskie zdefiniowane w interfejsie.  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 Należy zauważyć, że Klasa `customerInfo` używa `Implements` instrukcji w osobnym wierszu kodu źródłowego, aby wskazać, że klasa implementuje wszystkie elementy członkowskie `ICustomerInfo` interfejsu. Następnie każdy element członkowski w klasie używa `Implements` słowa kluczowego jako części deklaracji elementu członkowskiego, aby wskazać, że implementuje ten element członkowski interfejsu.  
  
## <a name="example"></a>Przykład  
 W poniższych dwóch procedurach pokazano, jak można użyć interfejsu zaimplementowanego w poprzednim przykładzie. Aby przetestować implementację, należy dodać te procedury do projektu i wywołać `testImplements` procedurę.  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Zobacz też

- [Implementuje](implements-clause.md)
- [Interface, instrukcja](interface-statement.md)
- [Interfejsy](../../programming-guide/language-features/interfaces/index.md)
