---
title: "Nie można wywołać funkcji zaprzyjaźnionej dla obiektu, który nie jest wystąpieniem klasy definiującej"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2f1ac1ea14efb0cdf0d8ca03257e4da33d35e368
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a>Nie można wywołać funkcji zaprzyjaźnionej dla obiektu, który nie jest wystąpieniem klasy definiującej
Albo próbował wywołać `Friend` procedury klasy lub użytkownik próbował uzyskać dostęp do `Friend` właściwości lub metody międzyprocesowa lub między wątkami. A `Friend` procedury z modułu poza klasą, ale jest częścią projektu, w którym klasa jest zdefiniowana.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że wywoływania lub uzyskiwania dostępu do procedury z moduł, który jest częścią projektu, w którym zdefiniowana jest klasa.  
  
## <a name="see-also"></a>Zobacz też  
 [Friend](../../visual-basic/language-reference/modifiers/friend.md)
