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
ms.openlocfilehash: 56d79691a216f87c847474ce4340b454850b9b11
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969703"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a><span data-ttu-id="d178a-102">Wykonywanie zadań z My.Application, My.Computer oraz My.User (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d178a-102">Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)</span></span>
<span data-ttu-id="d178a-103">Trzy centralnego `My` obiekty, które zapewniają dostęp do informacji i najczęściej używane funkcje są `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), a `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span><span class="sxs-lookup"><span data-stu-id="d178a-103">The three central `My` objects that provide access to information and commonly used functionality are `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), and `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span></span> <span data-ttu-id="d178a-104">Dostęp do informacji, który jest powiązany z bieżącej aplikacji, komputera, na którym aplikacja jest zainstalowana na lub z bieżącym użytkownikiem aplikacji, odpowiednio, można użyć tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="d178a-104">You can use these objects to access information that is related to the current application, the computer that the application is installed on, or the current user of the application, respectively.</span></span>  
  
## <a name="myapplication-mycomputer-and-myuser"></a><span data-ttu-id="d178a-105">My.Application, My.Computer oraz My.User</span><span class="sxs-lookup"><span data-stu-id="d178a-105">My.Application, My.Computer, and My.User</span></span>  
 <span data-ttu-id="d178a-106">W poniższych przykładach pokazano, jak informacje mogą być pobierane przy użyciu `My`.</span><span class="sxs-lookup"><span data-stu-id="d178a-106">The following examples demonstrate how information can be retrieved using `My`.</span></span>  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 <span data-ttu-id="d178a-107">Oprócz pobierania informacji o, elementy eksponowane przez te trzy obiekty pozwalają również na wykonywanie metod, które dotyczą tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="d178a-107">In addition to retrieving information, the members exposed through these three objects also allow you to execute methods related to that object.</span></span> <span data-ttu-id="d178a-108">Na przykład są dostępne różne metody do manipulowania plikami lub zaktualizuj rejestr za pośrednictwem `My.Computer`.</span><span class="sxs-lookup"><span data-stu-id="d178a-108">For instance, you can access a variety of methods to manipulate files or update the registry through `My.Computer`.</span></span>  
  
 <span data-ttu-id="d178a-109">We/Wy pliku jest znacznie łatwiejsze i szybsze działanie w przypadku `My`, który zawiera wiele różnych metod i właściwości do manipulowania w systemie plików, katalogów i dysków.</span><span class="sxs-lookup"><span data-stu-id="d178a-109">File I/O is significantly easier and faster with `My`, which includes a variety of methods and properties for manipulating files, directories, and drives.</span></span> <span data-ttu-id="d178a-110"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Obiekt umożliwia odczytywanie dużych plików ze strukturą, które mają rozdzielany lub stałej szerokości pola.</span><span class="sxs-lookup"><span data-stu-id="d178a-110">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object allows you to read from large structured files that have delimited or fixed-width fields.</span></span> <span data-ttu-id="d178a-111">W tym przykładzie otwiera `TextFieldParser` `reader` i używa ich do odczytu z `C:\TestFolder1\test1.txt`.</span><span class="sxs-lookup"><span data-stu-id="d178a-111">This example opens the `TextFieldParser` `reader` and uses it to read from `C:\TestFolder1\test1.txt`.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 <span data-ttu-id="d178a-112">`My.Application` Umożliwia zmianę kultury dla swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d178a-112">`My.Application` allows you to change the culture for your application.</span></span> <span data-ttu-id="d178a-113">W poniższym przykładzie pokazano, jak można wywołać tej metody.</span><span class="sxs-lookup"><span data-stu-id="d178a-113">The following example demonstrates how this method can be called.</span></span>  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="d178a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d178a-114">See also</span></span>
- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [<span data-ttu-id="d178a-115">Jak My zależy od typu projektu</span><span class="sxs-lookup"><span data-stu-id="d178a-115">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
