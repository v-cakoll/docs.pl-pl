---
title: 'Instrukcje: zmiana ustawień użytkownika'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: d24b6d239c894788ce67b0723b4bf034050bf307
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329628"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a><span data-ttu-id="5478a-102">Porady: zmienianie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5478a-102">How to: Change User Settings in Visual Basic</span></span>

<span data-ttu-id="5478a-103">Ustawienie użytkownika można zmienić, przypisując nową wartość do właściwości `My.Settings` ustawienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="5478a-103">You can change a user setting by assigning a new value to the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="5478a-104">Obiekt `My.Settings` udostępnia każde ustawienie jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="5478a-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="5478a-105">Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taki sam jak typ ustawienia.</span><span class="sxs-lookup"><span data-stu-id="5478a-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="5478a-106">Ustawienie **Scope** określa, czy właściwość jest tylko do odczytu: **Właściwość**dla application -scope ustawienie jest tylko do odczytu, podczas gdy właściwość dla **użytkownika**-scope ustawienie jest odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="5478a-106">The setting's **Scope** determines if the property is read-only: The property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="5478a-107">Aby uzyskać więcej informacji, zobacz [Obiekt My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="5478a-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5478a-108">Chociaż można zmienić i zapisać wartości ustawień zakresu użytkownika w czasie wykonywania, ustawienia zakresu aplikacji są tylko do odczytu i nie można zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="5478a-108">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="5478a-109">Ustawienia zakresu aplikacji można zmienić podczas tworzenia aplikacji przy użyciu **projektanta projektu** lub edytując plik konfiguracyjny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5478a-109">You can change application-scope settings when you create the application by using the **Project Designer** or by editing the application's configuration file.</span></span> <span data-ttu-id="5478a-110">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="5478a-110">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5478a-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="5478a-111">Example</span></span>  

 <span data-ttu-id="5478a-112">W tym przykładzie `Nickname` zmienia wartość ustawienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5478a-112">This example changes the value of the `Nickname` user setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 <span data-ttu-id="5478a-113">W tym przykładzie do pracy `Nickname` aplikacja musi mieć `String`ustawienie użytkownika, typu .</span><span class="sxs-lookup"><span data-stu-id="5478a-113">For this example to work, your application must have a `Nickname` user setting, of type `String`.</span></span>  
  
 <span data-ttu-id="5478a-114">Aplikacja zapisuje ustawienia użytkownika po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5478a-114">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="5478a-115">Aby natychmiast zapisać ustawienia, `My.Settings.Save` należy wywołać metodę.</span><span class="sxs-lookup"><span data-stu-id="5478a-115">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="5478a-116">Aby uzyskać więcej informacji, zobacz [Jak: Utrwalanie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="5478a-116">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5478a-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5478a-117">See also</span></span>

- [<span data-ttu-id="5478a-118">My.Settings, obiekt</span><span class="sxs-lookup"><span data-stu-id="5478a-118">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="5478a-119">Porady: odczytywanie ustawień aplikacji w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5478a-119">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="5478a-120">Porady: utrwalanie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5478a-120">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="5478a-121">Porady: tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5478a-121">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="5478a-122">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="5478a-122">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
