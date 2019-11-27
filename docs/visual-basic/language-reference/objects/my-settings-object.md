---
title: My.Settings — Obiekt
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 9560a51332ea596d4cf2228f1e07c158a0457ece
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350359"
---
# <a name="mysettings-object"></a><span data-ttu-id="b272d-102">My.Settings — Obiekt</span><span class="sxs-lookup"><span data-stu-id="b272d-102">My.Settings Object</span></span>
<span data-ttu-id="b272d-103">Udostępnia właściwości i metody dostępu do ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b272d-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b272d-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b272d-104">Remarks</span></span>  
 <span data-ttu-id="b272d-105">Obiekt `My.Settings` zapewnia dostęp do ustawień aplikacji i umożliwia dynamiczne przechowywanie i pobieranie ustawień właściwości oraz innych informacji dotyczących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b272d-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="b272d-106">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="b272d-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b272d-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b272d-107">Properties</span></span>  
 <span data-ttu-id="b272d-108">Właściwości obiektu `My.Settings` zapewniają dostęp do ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b272d-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="b272d-109">Aby dodać lub usunąć ustawienia, użyj **projektanta ustawień**.</span><span class="sxs-lookup"><span data-stu-id="b272d-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="b272d-110">Każde ustawienie ma **nazwę**, **typ**, **zakres**i **wartość**, a te ustawienia określają, jak Właściwość uzyskiwania dostępu do każdego ustawienia pojawia się w obiekcie `My.Settings`:</span><span class="sxs-lookup"><span data-stu-id="b272d-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
- <span data-ttu-id="b272d-111">**Nazwa** określa nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="b272d-111">**Name** determines the name of the property.</span></span>  
  
- <span data-ttu-id="b272d-112">**Typ** określa typ właściwości.</span><span class="sxs-lookup"><span data-stu-id="b272d-112">**Type** determines the type of the property.</span></span>  
  
- <span data-ttu-id="b272d-113">**Zakres** wskazuje, czy właściwość jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="b272d-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="b272d-114">Jeśli wartość jest **aplikacją**, właściwość jest tylko do odczytu; Jeśli wartość to **User**, właściwość jest do odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="b272d-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
- <span data-ttu-id="b272d-115">**Wartość** jest wartością domyślną właściwości.</span><span class="sxs-lookup"><span data-stu-id="b272d-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b272d-116">Metody</span><span class="sxs-lookup"><span data-stu-id="b272d-116">Methods</span></span>  
  
|<span data-ttu-id="b272d-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="b272d-117">Method</span></span>|<span data-ttu-id="b272d-118">Opis</span><span class="sxs-lookup"><span data-stu-id="b272d-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="b272d-119">Ponownie ładuje ustawienia użytkownika z ostatnio zapisanymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="b272d-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="b272d-120">Zapisuje bieżące ustawienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b272d-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="b272d-121">Obiekt `My.Settings` udostępnia także zaawansowane właściwości i metody dziedziczone z klasy <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="b272d-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="b272d-122">Zadania</span><span class="sxs-lookup"><span data-stu-id="b272d-122">Tasks</span></span>  
 <span data-ttu-id="b272d-123">W poniższej tabeli przedstawiono przykłady zadań związanych z obiektem `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="b272d-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="b272d-124">Do</span><span class="sxs-lookup"><span data-stu-id="b272d-124">To</span></span>|<span data-ttu-id="b272d-125">Zobacz</span><span class="sxs-lookup"><span data-stu-id="b272d-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="b272d-126">Odczyt ustawienia aplikacji</span><span class="sxs-lookup"><span data-stu-id="b272d-126">Read an application setting</span></span>|[<span data-ttu-id="b272d-127">Instrukcje: odczytywanie ustawień aplikacji w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b272d-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="b272d-128">Zmiana ustawienia użytkownika</span><span class="sxs-lookup"><span data-stu-id="b272d-128">Change a user setting</span></span>|[<span data-ttu-id="b272d-129">Instrukcje: Zmienianie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b272d-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="b272d-130">Utrwalanie ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="b272d-130">Persist user settings</span></span>|[<span data-ttu-id="b272d-131">Instrukcje: utrwalanie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b272d-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="b272d-132">Tworzenie siatki właściwości dla ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="b272d-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="b272d-133">Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b272d-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="b272d-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="b272d-134">Example</span></span>  
 <span data-ttu-id="b272d-135">Ten przykład wyświetla wartość ustawienia `Nickname`.</span><span class="sxs-lookup"><span data-stu-id="b272d-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="b272d-136">Aby ten przykład działał, aplikacja musi mieć ustawienie `Nickname` typu `String`.</span><span class="sxs-lookup"><span data-stu-id="b272d-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b272d-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b272d-137">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="b272d-138">Instrukcje: odczytywanie ustawień aplikacji w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b272d-138">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="b272d-139">Instrukcje: Zmienianie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b272d-139">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="b272d-140">Instrukcje: utrwalanie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b272d-140">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="b272d-141">Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b272d-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="b272d-142">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="b272d-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
