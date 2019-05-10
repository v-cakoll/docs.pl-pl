---
title: My.Settings — obiekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 9533e8e1ccc51078fefcf6bf73feb2683ae8febb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625280"
---
# <a name="mysettings-object"></a><span data-ttu-id="fda5a-102">My.Settings — Obiekt</span><span class="sxs-lookup"><span data-stu-id="fda5a-102">My.Settings Object</span></span>
<span data-ttu-id="fda5a-103">Udostępnia właściwości i metody dostępu do ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fda5a-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fda5a-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fda5a-104">Remarks</span></span>  
 <span data-ttu-id="fda5a-105">Obiekt `My.Settings` zapewnia dostęp do ustawień aplikacji i pozwala dynamicznie zapisywać oraz pobierać ustawienia właściwości i inne informacje dotyczące aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fda5a-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="fda5a-106">Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="fda5a-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fda5a-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="fda5a-107">Properties</span></span>  
 <span data-ttu-id="fda5a-108">Właściwości obiektu `My.Settings` zapewniają dostęp do ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fda5a-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="fda5a-109">Aby dodać lub usunąć ustawienia, należy użyć **Projektant ustawień**.</span><span class="sxs-lookup"><span data-stu-id="fda5a-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="fda5a-110">Każde ustawienie ma **nazwę**, **typ**, **zakres** i **wartość**. Ustawienia te określają, jak właściwość dostępu do każdego ustawienia wyświetla się w obiekcie `My.Settings`:</span><span class="sxs-lookup"><span data-stu-id="fda5a-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
- <span data-ttu-id="fda5a-111">**Nazwa** Określa nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="fda5a-111">**Name** determines the name of the property.</span></span>  
  
- <span data-ttu-id="fda5a-112">**Typ** Określa typ właściwości.</span><span class="sxs-lookup"><span data-stu-id="fda5a-112">**Type** determines the type of the property.</span></span>  
  
- <span data-ttu-id="fda5a-113">**Zakres** wskazuje, czy właściwość jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="fda5a-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="fda5a-114">Jeśli wartością jest **aplikacja**, właściwość jest tylko do odczytu. Jeśli wartością jest **użytkownik**, ta właściwość jest do odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="fda5a-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
- <span data-ttu-id="fda5a-115">**Wartość** jest wartością domyślną właściwości.</span><span class="sxs-lookup"><span data-stu-id="fda5a-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fda5a-116">Metody</span><span class="sxs-lookup"><span data-stu-id="fda5a-116">Methods</span></span>  
  
|<span data-ttu-id="fda5a-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="fda5a-117">Method</span></span>|<span data-ttu-id="fda5a-118">Opis</span><span class="sxs-lookup"><span data-stu-id="fda5a-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="fda5a-119">Ponownie ładuje ustawienia użytkownika z ostatnio zapisanymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="fda5a-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="fda5a-120">Zapisuje bieżące ustawienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fda5a-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="fda5a-121">Obiekt `My.Settings` udostępnia zaawansowane właściwości i metody odziedziczone z klasy <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="fda5a-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="fda5a-122">Zadania</span><span class="sxs-lookup"><span data-stu-id="fda5a-122">Tasks</span></span>  
 <span data-ttu-id="fda5a-123">W poniższej tabeli przedstawiono przykłady zadań z obiektem `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="fda5a-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="fda5a-124">Zadanie</span><span class="sxs-lookup"><span data-stu-id="fda5a-124">To</span></span>|<span data-ttu-id="fda5a-125">Zobacz</span><span class="sxs-lookup"><span data-stu-id="fda5a-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="fda5a-126">Odczyt ustawienia aplikacji</span><span class="sxs-lookup"><span data-stu-id="fda5a-126">Read an application setting</span></span>|[<span data-ttu-id="fda5a-127">Instrukcje: Odczytywanie ustawień aplikacji w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fda5a-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="fda5a-128">Zmiana ustawienia użytkownika</span><span class="sxs-lookup"><span data-stu-id="fda5a-128">Change a user setting</span></span>|[<span data-ttu-id="fda5a-129">Instrukcje: Zmienianie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fda5a-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="fda5a-130">Utrwalanie ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="fda5a-130">Persist user settings</span></span>|[<span data-ttu-id="fda5a-131">Instrukcje: Utrwalanie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fda5a-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="fda5a-132">Tworzenie siatki właściwości dla ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="fda5a-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="fda5a-133">Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fda5a-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="fda5a-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="fda5a-134">Example</span></span>  
 <span data-ttu-id="fda5a-135">W tym przykładzie jest wyświetlana wartość ustawienia `Nickname`.</span><span class="sxs-lookup"><span data-stu-id="fda5a-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="fda5a-136">Aby ten przykład działał, aplikacja musi mieć ustawienie `Nickname` typu `String`.</span><span class="sxs-lookup"><span data-stu-id="fda5a-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fda5a-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fda5a-137">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="fda5a-138">Instrukcje: Odczytywanie ustawień aplikacji w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fda5a-138">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="fda5a-139">Instrukcje: Zmienianie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fda5a-139">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="fda5a-140">Instrukcje: Utrwalanie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fda5a-140">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="fda5a-141">Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fda5a-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="fda5a-142">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="fda5a-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
