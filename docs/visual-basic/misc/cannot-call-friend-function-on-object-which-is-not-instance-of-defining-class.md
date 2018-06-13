---
title: Nie można wywołać funkcji zaprzyjaźnionej dla obiektu, który nie jest wystąpieniem klasy definiującej
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: a655207110d512805490b693e413b1d22b0367ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33634935"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a>Nie można wywołać funkcji zaprzyjaźnionej dla obiektu, który nie jest wystąpieniem klasy definiującej
Albo próbował wywołać `Friend` procedury klasy lub użytkownik próbował uzyskać dostęp do `Friend` właściwości lub metody międzyprocesowa lub między wątkami. A `Friend` procedury z modułu poza klasą, ale jest częścią projektu, w którym klasa jest zdefiniowana.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że wywoływania lub uzyskiwania dostępu do procedury z moduł, który jest częścią projektu, w którym zdefiniowana jest klasa.  
  
## <a name="see-also"></a>Zobacz też  
 [Friend](../../visual-basic/language-reference/modifiers/friend.md)
