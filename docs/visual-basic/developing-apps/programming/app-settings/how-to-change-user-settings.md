---
title: 'Instrukcje: Zmień ustawienia użytkownika w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: 553ebc5b0d6381f56783df8be83344f96a21dd8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968405"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a><span data-ttu-id="de1b8-102">Instrukcje: Zmień ustawienia użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="de1b8-102">How to: Change User Settings in Visual Basic</span></span>
<span data-ttu-id="de1b8-103">Ustawienie użytkownika można zmienić, przypisując nową wartość do właściwości ustawienia w `My.Settings` obiekcie.</span><span class="sxs-lookup"><span data-stu-id="de1b8-103">You can change a user setting by assigning a new value to the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="de1b8-104">`My.Settings` Obiekt uwidacznia każde ustawienie jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="de1b8-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="de1b8-105">Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taki sam jak typ ustawienia.</span><span class="sxs-lookup"><span data-stu-id="de1b8-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="de1b8-106">**Zakres** ustawienia określa, czy właściwość jest tylko do odczytu: Właściwość dla ustawienia zakresu **aplikacji**jest tylko do odczytu, podczas gdy właściwość dla ustawienia zakresu **użytkownika**ma wartość odczyt i zapis.</span><span class="sxs-lookup"><span data-stu-id="de1b8-106">The setting's **Scope** determines if the property is read-only: The property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="de1b8-107">Aby uzyskać więcej informacji, zobacz [My. Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="de1b8-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de1b8-108">Chociaż można zmienić i zapisać wartości ustawień zakresu użytkownika w czasie wykonywania, ustawienia zakresu aplikacji są tylko do odczytu i nie można ich programowo zmienić.</span><span class="sxs-lookup"><span data-stu-id="de1b8-108">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="de1b8-109">Ustawienia zakresu aplikacji można zmienić podczas tworzenia aplikacji za pomocą **projektanta projektu** lub edytując plik konfiguracyjny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de1b8-109">You can change application-scope settings when you create the application by using the **Project Designer** or by editing the application's configuration file.</span></span> <span data-ttu-id="de1b8-110">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="de1b8-110">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="de1b8-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="de1b8-111">Example</span></span>  
 <span data-ttu-id="de1b8-112">Ten przykład zmienia wartość `Nickname` ustawienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="de1b8-112">This example changes the value of the `Nickname` user setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 <span data-ttu-id="de1b8-113">Aby ten przykład działał, aplikacja musi mieć `Nickname` ustawienie użytkownika o typie. `String`</span><span class="sxs-lookup"><span data-stu-id="de1b8-113">For this example to work, your application must have a `Nickname` user setting, of type `String`.</span></span>  
  
 <span data-ttu-id="de1b8-114">Aplikacja zapisuje ustawienia użytkownika po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de1b8-114">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="de1b8-115">Aby natychmiast zapisać ustawienia, wywołaj `My.Settings.Save` metodę.</span><span class="sxs-lookup"><span data-stu-id="de1b8-115">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="de1b8-116">Aby uzyskać więcej informacji, zobacz [jak: Utrwalaj ustawienia użytkownika w](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="de1b8-116">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de1b8-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de1b8-117">See also</span></span>

- [<span data-ttu-id="de1b8-118">My.Settings, obiekt</span><span class="sxs-lookup"><span data-stu-id="de1b8-118">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="de1b8-119">Instrukcje: Odczytaj ustawienia aplikacji w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="de1b8-119">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="de1b8-120">Instrukcje: Utrwalanie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="de1b8-120">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="de1b8-121">Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="de1b8-121">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="de1b8-122">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="de1b8-122">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
