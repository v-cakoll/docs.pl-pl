---
title: Nie można wywołać funkcji zaprzyjaźnionej dla obiektu, który nie jest wystąpieniem klasy definiującej
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: c18c04470c4c49113e8195b92185326c5c4197c1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400851"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a>Nie można wywołać funkcji zaprzyjaźnionej dla obiektu, który nie jest wystąpieniem klasy definiującej
Podjęto próbę wywołania `Friend` procedury klasy lub nastąpiła próba uzyskania dostępu do `Friend` właściwości lub metody albo dla wielu wątków. `Friend`Procedura jest wywoływana z modułu poza klasą, ale jest częścią projektu, w którym jest zdefiniowana Klasa.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że wywołujesz lub uzyskujesz dostęp do procedury z modułu, który jest częścią projektu, w którym zdefiniowano klasę.  
  
## <a name="see-also"></a>Zobacz też

- [Osoby](../language-reference/modifiers/friend.md)
