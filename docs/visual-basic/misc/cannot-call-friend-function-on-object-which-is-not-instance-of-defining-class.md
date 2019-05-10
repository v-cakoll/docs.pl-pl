---
title: Nie można wywołać funkcji zaprzyjaźnionej dla obiektu, który nie jest wystąpieniem klasy definiującej
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: a227e5761bacc36c0682844a833e70c34582a5d3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622603"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a>Nie można wywołać funkcji zaprzyjaźnionej dla obiektu, który nie jest wystąpieniem klasy definiującej
Albo próbowaliśmy połączyć się z `Friend` procedury klasy lub użytkownik próbował uzyskać dostęp do `Friend` właściwość lub metoda między procesami lub między wątkami. A `Friend` procedura jest wywoływane z modułu poza klasą, ale jest częścią projektu, w którym klasa jest zdefiniowana.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że podczas wywoływania lub uzyskiwania dostępu do procedury z modułu, który jest częścią projektu, w którym zdefiniowano klasy.  
  
## <a name="see-also"></a>Zobacz także

- [Friend](../../visual-basic/language-reference/modifiers/friend.md)
