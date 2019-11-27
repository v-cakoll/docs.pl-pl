---
title: 'Instrukcje: odczytywanie ustawień aplikacji'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 04726381f8d285ae61045d1624b3b41b7f47e491
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329567"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="0de8c-102">Porady: odczytywanie ustawień aplikacji w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0de8c-102">How to: Read Application Settings in Visual Basic</span></span>

<span data-ttu-id="0de8c-103">Ustawienia użytkownika można odczytać, uzyskując dostęp do właściwości ustawienia w obiekcie `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="0de8c-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="0de8c-104">Obiekt `My.Settings` uwidacznia każde ustawienie jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="0de8c-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="0de8c-105">Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taki sam jak typ ustawienia.</span><span class="sxs-lookup"><span data-stu-id="0de8c-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="0de8c-106">**Zakres** ustawienia wskazuje, czy właściwość jest tylko do odczytu; Właściwość dla ustawienia zakresu **aplikacji** jest tylko do odczytu, podczas gdy właściwość dla zakresu **użytkownika** ma wartość odczyt-zapis.</span><span class="sxs-lookup"><span data-stu-id="0de8c-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="0de8c-107">Aby uzyskać więcej informacji, zobacz [My. Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="0de8c-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0de8c-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="0de8c-108">Example</span></span>  

 <span data-ttu-id="0de8c-109">Ten przykład wyświetla wartość ustawienia `Nickname`.</span><span class="sxs-lookup"><span data-stu-id="0de8c-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="0de8c-110">Aby ten przykład działał, aplikacja musi mieć ustawienie `Nickname` typu `String`.</span><span class="sxs-lookup"><span data-stu-id="0de8c-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="0de8c-111">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="0de8c-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0de8c-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0de8c-112">See also</span></span>

- [<span data-ttu-id="0de8c-113">My.Settings, obiekt</span><span class="sxs-lookup"><span data-stu-id="0de8c-113">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="0de8c-114">Instrukcje: Zmienianie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0de8c-114">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="0de8c-115">Instrukcje: utrwalanie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0de8c-115">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="0de8c-116">Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0de8c-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="0de8c-117">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="0de8c-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
