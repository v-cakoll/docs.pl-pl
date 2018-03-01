---
title: "My.Settings — Obiekt"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2f744460f8ea6c6c7f5c8c5e1658bd357e910def
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="mysettings-object"></a><span data-ttu-id="5daa9-102">My.Settings — Obiekt</span><span class="sxs-lookup"><span data-stu-id="5daa9-102">My.Settings Object</span></span>
<span data-ttu-id="5daa9-103">Udostępnia właściwości i metod dostępu do ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5daa9-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5daa9-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5daa9-104">Remarks</span></span>  
 <span data-ttu-id="5daa9-105">`My.Settings` Obiektu zapewnia dostęp do ustawień aplikacji i pozwala na dynamicznie przechowywać i pobierać ustawienia właściwości i inne informacje dotyczące aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5daa9-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="5daa9-106">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="5daa9-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5daa9-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5daa9-107">Properties</span></span>  
 <span data-ttu-id="5daa9-108">Właściwości `My.Settings` obiektu zapewniają dostęp do ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5daa9-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="5daa9-109">Aby dodać lub usunąć ustawienia, należy użyć **projektanta ustawień**.</span><span class="sxs-lookup"><span data-stu-id="5daa9-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="5daa9-110">Każdy ma **nazwa**, **typu**, **zakres**, i **wartość**, i te ustawienia określają, jak właściwości każdego ustawienia dostępu do zostanie wyświetlony w `My.Settings` obiektu:</span><span class="sxs-lookup"><span data-stu-id="5daa9-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
-   <span data-ttu-id="5daa9-111">**Nazwa** Określa nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="5daa9-111">**Name** determines the name of the property.</span></span>  
  
-   <span data-ttu-id="5daa9-112">**Typ** Określa typ właściwości.</span><span class="sxs-lookup"><span data-stu-id="5daa9-112">**Type** determines the type of the property.</span></span>  
  
-   <span data-ttu-id="5daa9-113">**Zakres** wskazuje, czy właściwość jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="5daa9-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="5daa9-114">Jeśli wartość jest **aplikacji**, właściwość jest tylko do odczytu; Jeśli wartość jest **użytkownika**, ta właściwość jest do odczytu / zapisu.</span><span class="sxs-lookup"><span data-stu-id="5daa9-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
-   <span data-ttu-id="5daa9-115">**Wartość** jest wartością domyślną właściwości.</span><span class="sxs-lookup"><span data-stu-id="5daa9-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5daa9-116">Metody</span><span class="sxs-lookup"><span data-stu-id="5daa9-116">Methods</span></span>  
  
|<span data-ttu-id="5daa9-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="5daa9-117">Method</span></span>|<span data-ttu-id="5daa9-118">Opis</span><span class="sxs-lookup"><span data-stu-id="5daa9-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="5daa9-119">Ponownie ładuje ustawienia użytkownika z ostatnio zapisane wartości.</span><span class="sxs-lookup"><span data-stu-id="5daa9-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="5daa9-120">Zapisuje bieżące ustawienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5daa9-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="5daa9-121">`My.Settings` Obiektu udostępnia zaawansowane właściwości i metod odziedziczone <xref:System.Configuration.ApplicationSettingsBase> klasy.</span><span class="sxs-lookup"><span data-stu-id="5daa9-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="5daa9-122">Zadania</span><span class="sxs-lookup"><span data-stu-id="5daa9-122">Tasks</span></span>  
 <span data-ttu-id="5daa9-123">W poniższej tabeli przedstawiono przykłady dotyczące zadań `My.Settings` obiektu.</span><span class="sxs-lookup"><span data-stu-id="5daa9-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="5daa9-124">Do</span><span class="sxs-lookup"><span data-stu-id="5daa9-124">To</span></span>|<span data-ttu-id="5daa9-125">Zobacz</span><span class="sxs-lookup"><span data-stu-id="5daa9-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="5daa9-126">Ustawienie aplikacji do odczytu</span><span class="sxs-lookup"><span data-stu-id="5daa9-126">Read an application setting</span></span>|[<span data-ttu-id="5daa9-127">Porady: odczytywanie ustawień aplikacji w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5daa9-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="5daa9-128">Zmień ustawienia użytkownika</span><span class="sxs-lookup"><span data-stu-id="5daa9-128">Change a user setting</span></span>|[<span data-ttu-id="5daa9-129">Porady: Zmienianie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5daa9-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="5daa9-130">Utrwalanie ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="5daa9-130">Persist user settings</span></span>|[<span data-ttu-id="5daa9-131">Porady: utrwalanie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5daa9-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="5daa9-132">Tworzenie siatki właściwości dla ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="5daa9-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="5daa9-133">Porady: tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5daa9-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="5daa9-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="5daa9-134">Example</span></span>  
 <span data-ttu-id="5daa9-135">W tym przykładzie wyświetlono wartości `Nickname` ustawienie.</span><span class="sxs-lookup"><span data-stu-id="5daa9-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]  
  
 <span data-ttu-id="5daa9-136">W tym przykładzie działała, aplikacja musi mieć `Nickname` ustawienia typu `String`.</span><span class="sxs-lookup"><span data-stu-id="5daa9-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5daa9-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5daa9-137">See Also</span></span>  
 <xref:System.Configuration.ApplicationSettingsBase>  
 [<span data-ttu-id="5daa9-138">Porady: odczytywanie ustawień aplikacji w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5daa9-138">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [<span data-ttu-id="5daa9-139">Porady: Zmienianie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5daa9-139">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [<span data-ttu-id="5daa9-140">Porady: utrwalanie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5daa9-140">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [<span data-ttu-id="5daa9-141">Porady: tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5daa9-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [<span data-ttu-id="5daa9-142">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="5daa9-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
