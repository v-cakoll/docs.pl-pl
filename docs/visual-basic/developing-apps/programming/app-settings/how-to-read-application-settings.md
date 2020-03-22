---
title: 'Instrukcje: odczytywanie ustawień aplikacji'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 04726381f8d285ae61045d1624b3b41b7f47e491
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329567"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="effe7-102">Porady: odczytywanie ustawień aplikacji w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="effe7-102">How to: Read Application Settings in Visual Basic</span></span>

<span data-ttu-id="effe7-103">Ustawienie użytkownika można odczytać, uzyskując dostęp do `My.Settings` właściwości ustawienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="effe7-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="effe7-104">Obiekt `My.Settings` udostępnia każde ustawienie jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="effe7-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="effe7-105">Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taki sam jak typ ustawienia.</span><span class="sxs-lookup"><span data-stu-id="effe7-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="effe7-106">Ustawienie **Scope** wskazuje, czy właściwość jest tylko do odczytu; właściwość dla application **scope** ustawienie jest tylko do odczytu, podczas gdy właściwość dla ustawienia zakresu **użytkownika** jest odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="effe7-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="effe7-107">Aby uzyskać więcej informacji, zobacz [Obiekt My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="effe7-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="effe7-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="effe7-108">Example</span></span>  

 <span data-ttu-id="effe7-109">W tym przykładzie `Nickname` wyświetlana jest wartość ustawienia.</span><span class="sxs-lookup"><span data-stu-id="effe7-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="effe7-110">W tym przykładzie do pracy, `Nickname` aplikacja musi `String`mieć ustawienie typu .</span><span class="sxs-lookup"><span data-stu-id="effe7-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="effe7-111">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="effe7-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="effe7-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="effe7-112">See also</span></span>

- [<span data-ttu-id="effe7-113">My.Settings, obiekt</span><span class="sxs-lookup"><span data-stu-id="effe7-113">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="effe7-114">Porady: zmienianie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="effe7-114">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="effe7-115">Porady: utrwalanie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="effe7-115">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="effe7-116">Porady: tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="effe7-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="effe7-117">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="effe7-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
