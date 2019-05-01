---
title: My.Settings — obiekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: a962f7cce961b1ee6829702a6815ba02c534efb4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050314"
---
# <a name="mysettings-object"></a><span data-ttu-id="5d974-102">My.Settings — Obiekt</span><span class="sxs-lookup"><span data-stu-id="5d974-102">My.Settings Object</span></span>
<span data-ttu-id="5d974-103">Udostępnia właściwości i metody dostępu do ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d974-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d974-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d974-104">Remarks</span></span>  
 <span data-ttu-id="5d974-105">Obiekt `My.Settings` zapewnia dostęp do ustawień aplikacji i pozwala dynamicznie zapisywać oraz pobierać ustawienia właściwości i inne informacje dotyczące aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d974-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="5d974-106">Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="5d974-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5d974-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5d974-107">Properties</span></span>  
 <span data-ttu-id="5d974-108">Właściwości obiektu `My.Settings` zapewniają dostęp do ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d974-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="5d974-109">Aby dodać lub usunąć ustawienia, należy użyć **Projektant ustawień**.</span><span class="sxs-lookup"><span data-stu-id="5d974-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="5d974-110">Każde ustawienie ma **nazwę**, **typ**, **zakres** i **wartość**. Ustawienia te określają, jak właściwość dostępu do każdego ustawienia wyświetla się w obiekcie `My.Settings`:</span><span class="sxs-lookup"><span data-stu-id="5d974-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
- <span data-ttu-id="5d974-111">**Nazwa** Określa nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="5d974-111">**Name** determines the name of the property.</span></span>  
  
- <span data-ttu-id="5d974-112">**Typ** Określa typ właściwości.</span><span class="sxs-lookup"><span data-stu-id="5d974-112">**Type** determines the type of the property.</span></span>  
  
- <span data-ttu-id="5d974-113">**Zakres** wskazuje, czy właściwość jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="5d974-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="5d974-114">Jeśli wartością jest **aplikacja**, właściwość jest tylko do odczytu. Jeśli wartością jest **użytkownik**, ta właściwość jest do odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="5d974-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
- <span data-ttu-id="5d974-115">**Wartość** jest wartością domyślną właściwości.</span><span class="sxs-lookup"><span data-stu-id="5d974-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d974-116">Metody</span><span class="sxs-lookup"><span data-stu-id="5d974-116">Methods</span></span>  
  
|<span data-ttu-id="5d974-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="5d974-117">Method</span></span>|<span data-ttu-id="5d974-118">Opis</span><span class="sxs-lookup"><span data-stu-id="5d974-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="5d974-119">Ponownie ładuje ustawienia użytkownika z ostatnio zapisanymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="5d974-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="5d974-120">Zapisuje bieżące ustawienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5d974-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="5d974-121">Obiekt `My.Settings` udostępnia zaawansowane właściwości i metody odziedziczone z klasy <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="5d974-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="5d974-122">Zadania</span><span class="sxs-lookup"><span data-stu-id="5d974-122">Tasks</span></span>  
 <span data-ttu-id="5d974-123">W poniższej tabeli przedstawiono przykłady zadań z obiektem `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="5d974-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="5d974-124">Zadanie</span><span class="sxs-lookup"><span data-stu-id="5d974-124">To</span></span>|<span data-ttu-id="5d974-125">Zobacz</span><span class="sxs-lookup"><span data-stu-id="5d974-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="5d974-126">Odczyt ustawienia aplikacji</span><span class="sxs-lookup"><span data-stu-id="5d974-126">Read an application setting</span></span>|[<span data-ttu-id="5d974-127">Instrukcje: Odczytywanie ustawień aplikacji w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d974-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="5d974-128">Zmiana ustawienia użytkownika</span><span class="sxs-lookup"><span data-stu-id="5d974-128">Change a user setting</span></span>|[<span data-ttu-id="5d974-129">Instrukcje: Zmienianie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d974-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="5d974-130">Utrwalanie ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="5d974-130">Persist user settings</span></span>|[<span data-ttu-id="5d974-131">Instrukcje: Utrwalanie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d974-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="5d974-132">Tworzenie siatki właściwości dla ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="5d974-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="5d974-133">Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d974-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="5d974-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d974-134">Example</span></span>  
 <span data-ttu-id="5d974-135">W tym przykładzie jest wyświetlana wartość ustawienia `Nickname`.</span><span class="sxs-lookup"><span data-stu-id="5d974-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="5d974-136">Aby ten przykład działał, aplikacja musi mieć ustawienie `Nickname` typu `String`.</span><span class="sxs-lookup"><span data-stu-id="5d974-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d974-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d974-137">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="5d974-138">Instrukcje: Odczytywanie ustawień aplikacji w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d974-138">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="5d974-139">Instrukcje: Zmienianie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d974-139">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="5d974-140">Instrukcje: Utrwalanie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d974-140">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="5d974-141">Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d974-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="5d974-142">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="5d974-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
