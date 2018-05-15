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
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a><span data-ttu-id="dffa7-102">Wykonywanie zadań z My.Application, My.Computer oraz My.User (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dffa7-102">Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)</span></span>
<span data-ttu-id="dffa7-103">Trzy centralnego `My` obiekty, które zapewniają dostęp do informacji i często używane funkcje są `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), a `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span><span class="sxs-lookup"><span data-stu-id="dffa7-103">The three central `My` objects that provide access to information and commonly used functionality are `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), and `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span></span> <span data-ttu-id="dffa7-104">Uzyskiwać dostęp do informacji związanych z bieżącej aplikacji, komputera, na którym aplikacja jest zainstalowana na lub z bieżącym użytkownikiem aplikacji, odpowiednio, można użyć tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="dffa7-104">You can use these objects to access information that is related to the current application, the computer that the application is installed on, or the current user of the application, respectively.</span></span>  
  
## <a name="myapplication-mycomputer-and-myuser"></a><span data-ttu-id="dffa7-105">My.Application, My.Computer oraz My.User</span><span class="sxs-lookup"><span data-stu-id="dffa7-105">My.Application, My.Computer, and My.User</span></span>  
 <span data-ttu-id="dffa7-106">W poniższych przykładach pokazano, jak informacje mogą być pobrany przy użyciu `My`.</span><span class="sxs-lookup"><span data-stu-id="dffa7-106">The following examples demonstrate how information can be retrieved using `My`.</span></span>  
  
 [!code-vb[VbVbcnMy#1](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]  
  
 [!code-vb[VbVbcnMy#2](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]  
  
 <span data-ttu-id="dffa7-107">Oprócz pobierania informacji o, elementy członkowskie udostępnione przez te trzy obiekty pozwalają również na wykonywanie metod dotyczących tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="dffa7-107">In addition to retrieving information, the members exposed through these three objects also allow you to execute methods related to that object.</span></span> <span data-ttu-id="dffa7-108">Można na przykład dostęp do różnych metod do obsługi plików i zaktualizować rejestru za pomocą `My.Computer`.</span><span class="sxs-lookup"><span data-stu-id="dffa7-108">For instance, you can access a variety of methods to manipulate files or update the registry through `My.Computer`.</span></span>  
  
 <span data-ttu-id="dffa7-109">We/Wy pliku jest znacznie łatwiejsze i szybsze z `My`, która obejmuje różne metody i właściwości do manipulowania plików, katalogów i dyskach.</span><span class="sxs-lookup"><span data-stu-id="dffa7-109">File I/O is significantly easier and faster with `My`, which includes a variety of methods and properties for manipulating files, directories, and drives.</span></span> <span data-ttu-id="dffa7-110"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Obiektu umożliwia odczytanie z dużych plików strukturalnych, które zostały rozdzielone lub pola o stałej szerokości.</span><span class="sxs-lookup"><span data-stu-id="dffa7-110">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object allows you to read from large structured files that have delimited or fixed-width fields.</span></span> <span data-ttu-id="dffa7-111">W tym przykładzie otwiera `TextFieldParser``reader` i używa go do odczytu z `C:\TestFolder1\test1.txt`.</span><span class="sxs-lookup"><span data-stu-id="dffa7-111">This example opens the `TextFieldParser``reader` and uses it to read from `C:\TestFolder1\test1.txt`.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#23](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]  
  
 <span data-ttu-id="dffa7-112">`My.Application` Umożliwia zmianę kultura dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dffa7-112">`My.Application` allows you to change the culture for your application.</span></span> <span data-ttu-id="dffa7-113">W poniższym przykładzie pokazano, jak można wywołać tej metody.</span><span class="sxs-lookup"><span data-stu-id="dffa7-113">The following example demonstrates how this method can be called.</span></span>  
  
 [!code-vb[VbVbcnMy#3](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="dffa7-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dffa7-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [<span data-ttu-id="dffa7-115">Jak My zależy od typu projektu</span><span class="sxs-lookup"><span data-stu-id="dffa7-115">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
