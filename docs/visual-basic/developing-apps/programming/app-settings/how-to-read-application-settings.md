---
title: 'Instrukcje: Odczytywanie ustawień aplikacji w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 032e06e674f2298d68f879f3ad474c79e3ff02db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659500"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="ecf31-102">Instrukcje: Odczytywanie ustawień aplikacji w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ecf31-102">How to: Read Application Settings in Visual Basic</span></span>
<span data-ttu-id="ecf31-103">Ustawienia użytkownika może być odczytany przez uzyskiwanie dostępu do właściwości ustawienia na `My.Settings` obiektu.</span><span class="sxs-lookup"><span data-stu-id="ecf31-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="ecf31-104">`My.Settings` Obiekt udostępnia każdego ustawienia jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="ecf31-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="ecf31-105">Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taka sama jak typ ustawienia.</span><span class="sxs-lookup"><span data-stu-id="ecf31-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="ecf31-106">Ustawienie **zakres** wskazuje, czy właściwość jest tylko do odczytu; właściwość dla **aplikacji** ustawienie zakresu jest tylko do odczytu, podczas właściwość dla **użytkownika** ustawienie zakresu jest do odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="ecf31-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="ecf31-107">Aby uzyskać więcej informacji, zobacz [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="ecf31-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecf31-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="ecf31-108">Example</span></span>  
 <span data-ttu-id="ecf31-109">W tym przykładzie jest wyświetlana wartość ustawienia `Nickname`.</span><span class="sxs-lookup"><span data-stu-id="ecf31-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-read-application-settings_1.vb)]  
  
 <span data-ttu-id="ecf31-110">Aby ten przykład działał, aplikacja musi mieć ustawienie `Nickname` typu `String`.</span><span class="sxs-lookup"><span data-stu-id="ecf31-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="ecf31-111">Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="ecf31-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecf31-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ecf31-112">See also</span></span>
- [<span data-ttu-id="ecf31-113">My.Settings, obiekt</span><span class="sxs-lookup"><span data-stu-id="ecf31-113">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="ecf31-114">Instrukcje: Zmienianie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ecf31-114">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="ecf31-115">Instrukcje: Utrwalanie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ecf31-115">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="ecf31-116">Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ecf31-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="ecf31-117">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="ecf31-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
