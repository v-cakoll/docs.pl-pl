---
title: 'Instrukcje: Odczytywanie ustawień aplikacji'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 9b326341c54d652479776e3ab93a2b140f4531e0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410143"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="29b69-102">Porady: odczytywanie ustawień aplikacji w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29b69-102">How to: Read Application Settings in Visual Basic</span></span>

<span data-ttu-id="29b69-103">Ustawienia użytkownika można odczytać, uzyskując dostęp do właściwości ustawienia w `My.Settings` obiekcie.</span><span class="sxs-lookup"><span data-stu-id="29b69-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="29b69-104">`My.Settings`Obiekt uwidacznia każde ustawienie jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="29b69-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="29b69-105">Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taki sam jak typ ustawienia.</span><span class="sxs-lookup"><span data-stu-id="29b69-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="29b69-106">**Zakres** ustawienia wskazuje, czy właściwość jest tylko do odczytu; Właściwość dla ustawienia zakresu **aplikacji** jest tylko do odczytu, podczas gdy właściwość dla zakresu **użytkownika** ma wartość odczyt-zapis.</span><span class="sxs-lookup"><span data-stu-id="29b69-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="29b69-107">Aby uzyskać więcej informacji, zobacz [My. Settings Object](../../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="29b69-107">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="29b69-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="29b69-108">Example</span></span>  

 <span data-ttu-id="29b69-109">Ten przykład wyświetla wartość `Nickname` Ustawienia.</span><span class="sxs-lookup"><span data-stu-id="29b69-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="29b69-110">Aby ten przykład działał, aplikacja musi mieć `Nickname` ustawienie typu `String` .</span><span class="sxs-lookup"><span data-stu-id="29b69-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="29b69-111">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="29b69-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29b69-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29b69-112">See also</span></span>

- [<span data-ttu-id="29b69-113">My.Settings — Obiekt</span><span class="sxs-lookup"><span data-stu-id="29b69-113">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="29b69-114">Porady: zmienianie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29b69-114">How to: Change User Settings in Visual Basic</span></span>](how-to-change-user-settings.md)
- [<span data-ttu-id="29b69-115">Porady: utrwalanie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29b69-115">How to: Persist User Settings in Visual Basic</span></span>](how-to-persist-user-settings.md)
- [<span data-ttu-id="29b69-116">Porady: tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29b69-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="29b69-117">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="29b69-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
