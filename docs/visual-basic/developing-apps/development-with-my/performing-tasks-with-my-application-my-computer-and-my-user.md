---
title: Wykonywanie zadań z My.Application, My.Computer oraz My.User (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
ms.openlocfilehash: 84ac57bf1bcf60664e2b18fed16a3bbe6c03dc68
ms.sourcegitcommit: bd4fa78f5a46133efdead1bc692a9aa2811d7868
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2018
ms.locfileid: "42755011"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a>Wykonywanie zadań z My.Application, My.Computer oraz My.User (Visual Basic)
Trzy centralnego `My` obiekty, które zapewniają dostęp do informacji i najczęściej używane funkcje są `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), a `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>). Dostęp do informacji, który jest powiązany z bieżącej aplikacji, komputera, na którym aplikacja jest zainstalowana na lub z bieżącym użytkownikiem aplikacji, odpowiednio, można użyć tych obiektów.  
  
## <a name="myapplication-mycomputer-and-myuser"></a>My.Application, My.Computer oraz My.User  
 W poniższych przykładach pokazano, jak informacje mogą być pobierane przy użyciu `My`.  
  
 [!code-vb[VbVbcnMy#1](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]  
  
 [!code-vb[VbVbcnMy#2](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]  
  
 Oprócz pobierania informacji o, elementy eksponowane przez te trzy obiekty pozwalają również na wykonywanie metod, które dotyczą tego obiektu. Na przykład są dostępne różne metody do manipulowania plikami lub zaktualizuj rejestr za pośrednictwem `My.Computer`.  
  
 We/Wy pliku jest znacznie łatwiejsze i szybsze działanie w przypadku `My`, który zawiera wiele różnych metod i właściwości do manipulowania w systemie plików, katalogów i dysków. <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Obiekt umożliwia odczytywanie dużych plików ze strukturą, które mają rozdzielany lub stałej szerokości pola. W tym przykładzie otwiera `TextFieldParser` `reader` i używa ich do odczytu z `C:\TestFolder1\test1.txt`.  
  
 [!code-vb[VbVbalrTextFieldParser#23](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]  
  
 `My.Application` Umożliwia zmianę kultury dla swojej aplikacji. W poniższym przykładzie pokazano, jak można wywołać tej metody.  
  
 [!code-vb[VbVbcnMy#3](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [Jak My zależy od typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
