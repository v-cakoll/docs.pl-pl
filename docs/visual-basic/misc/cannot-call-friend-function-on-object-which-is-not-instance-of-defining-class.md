---
title: Nie można wywołać funkcji zaprzyjaźnionej dla obiektu, który nie jest wystąpieniem klasy definiującej
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: c65bbb5028cf042b702bb2b8336d40512c980790
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912694"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a>Nie można wywołać funkcji zaprzyjaźnionej dla obiektu, który nie jest wystąpieniem klasy definiującej
Albo próbowaliśmy połączyć się z `Friend` procedury klasy lub użytkownik próbował uzyskać dostęp do `Friend` właściwość lub metoda między procesami lub między wątkami. A `Friend` procedura jest wywoływane z modułu poza klasą, ale jest częścią projektu, w którym klasa jest zdefiniowana.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że podczas wywoływania lub uzyskiwania dostępu do procedury z modułu, który jest częścią projektu, w którym zdefiniowano klasy.  
  
## <a name="see-also"></a>Zobacz także

- [Friend](../../visual-basic/language-reference/modifiers/friend.md)
