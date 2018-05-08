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
ms.openlocfilehash: bc2b0521598c00cdb398d936d61d65874a9cf274
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a>Wykonywanie zadań z My.Application, My.Computer oraz My.User (Visual Basic)
Trzy centralnego `My` obiekty, które zapewniają dostęp do informacji i często używane funkcje są `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), a `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>). Uzyskiwać dostęp do informacji związanych z bieżącej aplikacji, komputera, na którym aplikacja jest zainstalowana na lub z bieżącym użytkownikiem aplikacji, odpowiednio, można użyć tych obiektów.  
  
## <a name="myapplication-mycomputer-and-myuser"></a>My.Application, My.Computer oraz My.User  
 W poniższych przykładach pokazano, jak informacje mogą być pobrany przy użyciu `My`.  
  
 [!code-vb[VbVbcnMy#1](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]  
  
 [!code-vb[VbVbcnMy#2](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]  
  
 Oprócz pobierania informacji o, elementy członkowskie udostępnione przez te trzy obiekty pozwalają również na wykonywanie metod dotyczących tego obiektu. Można na przykład dostęp do różnych metod do obsługi plików i zaktualizować rejestru za pomocą `My.Computer`.  
  
 We/Wy pliku jest znacznie łatwiejsze i szybsze z `My`, która obejmuje różne metody i właściwości do manipulowania plików, katalogów i dyskach. <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Obiektu umożliwia odczytanie z dużych plików strukturalnych, które zostały rozdzielone lub pola o stałej szerokości. W tym przykładzie otwiera `TextFieldParser``reader` i używa go do odczytu z `C:\TestFolder1\test1.txt`.  
  
 [!code-vb[VbVbalrTextFieldParser#23](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]  
  
 `My.Application` Umożliwia zmianę kultura dla aplikacji. W poniższym przykładzie pokazano, jak można wywołać tej metody.  
  
 [!code-vb[VbVbcnMy#3](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [Jak My zależy od typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
