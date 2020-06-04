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
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a><span data-ttu-id="e39b7-102">Wykonywanie zadań z My.Application, My.Computer oraz My.User (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e39b7-102">Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)</span></span>

<span data-ttu-id="e39b7-103">Trzy centralne `My` obiekty, które zapewniają dostęp do informacji i powszechnie używane funkcje to `My.Application` ( <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> ), `My.Computer` ( <xref:Microsoft.VisualBasic.Devices.Computer> ) i `My.User` ( <xref:Microsoft.VisualBasic.ApplicationServices.User> ).</span><span class="sxs-lookup"><span data-stu-id="e39b7-103">The three central `My` objects that provide access to information and commonly used functionality are `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), and `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span></span> <span data-ttu-id="e39b7-104">Za pomocą tych obiektów można uzyskać dostęp do informacji związanych z bieżącą aplikacją, komputerze, na którym aplikacja jest zainstalowana, lub bieżącego użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e39b7-104">You can use these objects to access information that is related to the current application, the computer that the application is installed on, or the current user of the application, respectively.</span></span>  
  
## <a name="myapplication-mycomputer-and-myuser"></a><span data-ttu-id="e39b7-105">My. Application, my. Computer i my. User</span><span class="sxs-lookup"><span data-stu-id="e39b7-105">My.Application, My.Computer, and My.User</span></span>  

 <span data-ttu-id="e39b7-106">W poniższych przykładach pokazano, jak można pobrać informacje za pomocą polecenia `My` .</span><span class="sxs-lookup"><span data-stu-id="e39b7-106">The following examples demonstrate how information can be retrieved using `My`.</span></span>  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 <span data-ttu-id="e39b7-107">Oprócz pobierania informacji, elementy udostępniane za pomocą tych trzech obiektów umożliwiają również wykonywanie metod związanych z tym obiektem.</span><span class="sxs-lookup"><span data-stu-id="e39b7-107">In addition to retrieving information, the members exposed through these three objects also allow you to execute methods related to that object.</span></span> <span data-ttu-id="e39b7-108">Na przykład możesz uzyskać dostęp do różnych metod, aby manipulować plikami lub aktualizować rejestr za pomocą programu `My.Computer` .</span><span class="sxs-lookup"><span data-stu-id="e39b7-108">For instance, you can access a variety of methods to manipulate files or update the registry through `My.Computer`.</span></span>  
  
 <span data-ttu-id="e39b7-109">Operacje we/wy plików są znacznie łatwiejsze i szybsze dzięki `My` programowi, który obejmuje różne metody i właściwości służące do manipulowania plikami, katalogami i dyskami.</span><span class="sxs-lookup"><span data-stu-id="e39b7-109">File I/O is significantly easier and faster with `My`, which includes a variety of methods and properties for manipulating files, directories, and drives.</span></span> <span data-ttu-id="e39b7-110"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser>Obiekt umożliwia odczytywanie z dużych plików ze strukturą, które mają pola rozdzielone lub o stałej szerokości.</span><span class="sxs-lookup"><span data-stu-id="e39b7-110">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object allows you to read from large structured files that have delimited or fixed-width fields.</span></span> <span data-ttu-id="e39b7-111">Ten przykład otwiera `TextFieldParser` `reader` i używa go do odczytu z `C:\TestFolder1\test1.txt` .</span><span class="sxs-lookup"><span data-stu-id="e39b7-111">This example opens the `TextFieldParser` `reader` and uses it to read from `C:\TestFolder1\test1.txt`.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 <span data-ttu-id="e39b7-112">`My.Application`pozwala zmienić kulturę dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e39b7-112">`My.Application` allows you to change the culture for your application.</span></span> <span data-ttu-id="e39b7-113">Poniższy przykład ilustruje, jak ta metoda może być wywoływana.</span><span class="sxs-lookup"><span data-stu-id="e39b7-113">The following example demonstrates how this method can be called.</span></span>  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e39b7-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e39b7-114">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [<span data-ttu-id="e39b7-115">Jak My zależy od typu projektu</span><span class="sxs-lookup"><span data-stu-id="e39b7-115">How My Depends on Project Type</span></span>](how-my-depends-on-project-type.md)
