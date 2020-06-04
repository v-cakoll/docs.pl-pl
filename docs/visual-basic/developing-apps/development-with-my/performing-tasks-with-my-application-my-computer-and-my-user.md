---
title: Wykonywanie zadań z My.Application, My.Computer oraz My.User
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
ms.openlocfilehash: 55961d6857b690fc2726f541df8a5497a3207928
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411697"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a>Wykonywanie zadań z My.Application, My.Computer oraz My.User (Visual Basic)

Trzy centralne `My` obiekty, które zapewniają dostęp do informacji i powszechnie używane funkcje to `My.Application` ( <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> ), `My.Computer` ( <xref:Microsoft.VisualBasic.Devices.Computer> ) i `My.User` ( <xref:Microsoft.VisualBasic.ApplicationServices.User> ). Za pomocą tych obiektów można uzyskać dostęp do informacji związanych z bieżącą aplikacją, komputerze, na którym aplikacja jest zainstalowana, lub bieżącego użytkownika aplikacji.  
  
## <a name="myapplication-mycomputer-and-myuser"></a>My. Application, my. Computer i my. User  

 W poniższych przykładach pokazano, jak można pobrać informacje za pomocą polecenia `My` .  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 Oprócz pobierania informacji, elementy udostępniane za pomocą tych trzech obiektów umożliwiają również wykonywanie metod związanych z tym obiektem. Na przykład możesz uzyskać dostęp do różnych metod, aby manipulować plikami lub aktualizować rejestr za pomocą programu `My.Computer` .  
  
 Operacje we/wy plików są znacznie łatwiejsze i szybsze dzięki `My` programowi, który obejmuje różne metody i właściwości służące do manipulowania plikami, katalogami i dyskami. <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>Obiekt umożliwia odczytywanie z dużych plików ze strukturą, które mają pola rozdzielone lub o stałej szerokości. Ten przykład otwiera `TextFieldParser` `reader` i używa go do odczytu z `C:\TestFolder1\test1.txt` .  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 `My.Application`pozwala zmienić kulturę dla aplikacji. Poniższy przykład ilustruje, jak ta metoda może być wywoływana.  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Jak My zależy od typu projektu](how-my-depends-on-project-type.md)
