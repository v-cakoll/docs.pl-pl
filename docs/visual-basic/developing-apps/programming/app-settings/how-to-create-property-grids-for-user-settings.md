---
title: 'Instrukcje: tworzenie siatek właściwości dla ustawień użytkownika'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: bed4e8a2b50f0115c3b8d9d6abf427df5f216388
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329610"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="42e0c-102">Porady: tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42e0c-102">How to: Create Property Grids for User Settings in Visual Basic</span></span>

<span data-ttu-id="42e0c-103">Siatkę właściwości dla ustawień użytkownika można utworzyć, wypełniając formant <xref:System.Windows.Forms.PropertyGrid> właściwości `My.Settings` ustawieniami użytkownika obiektu.</span><span class="sxs-lookup"><span data-stu-id="42e0c-103">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42e0c-104">Aby ten przykład działał, aplikacja musi mieć skonfigurowane ustawienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="42e0c-104">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="42e0c-105">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="42e0c-105">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="42e0c-106">Obiekt `My.Settings` udostępnia każde ustawienie jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="42e0c-106">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="42e0c-107">Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taki sam jak typ ustawienia.</span><span class="sxs-lookup"><span data-stu-id="42e0c-107">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="42e0c-108">Zakres ustawienia **określa,** czy właściwość jest tylko do odczytu; właściwość dla **application**-scope ustawienie jest tylko do odczytu, podczas gdy właściwość dla **użytkownika**-scope ustawienie jest odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="42e0c-108">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="42e0c-109">Aby uzyskać więcej informacji, zobacz [Obiekt My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="42e0c-109">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42e0c-110">Nie można zmienić ani zapisać wartości ustawień zakresu aplikacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="42e0c-110">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="42e0c-111">Ustawienia zakresu aplikacji można zmienić tylko podczas tworzenia aplikacji (za pośrednictwem **projektanta projektu)** lub przez edycję pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="42e0c-111">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="42e0c-112">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="42e0c-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="42e0c-113">W tym przykładzie <xref:System.Windows.Forms.PropertyGrid> użyto formantu, aby `My.Settings` uzyskać dostęp do właściwości ustawień użytkownika obiektu.</span><span class="sxs-lookup"><span data-stu-id="42e0c-113">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="42e0c-114">Domyślnie <xref:System.Windows.Forms.PropertyGrid> pokazuje wszystkie właściwości `My.Settings` obiektu.</span><span class="sxs-lookup"><span data-stu-id="42e0c-114">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="42e0c-115">Jednak właściwości ustawienia użytkownika mają <xref:System.Configuration.UserScopedSettingAttribute> atrybut.</span><span class="sxs-lookup"><span data-stu-id="42e0c-115">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="42e0c-116">W tym <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> przykładzie <xref:System.Windows.Forms.PropertyGrid> ustawia <xref:System.Configuration.UserScopedSettingAttribute> właściwość do wyświetlania tylko właściwości ustawienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="42e0c-116">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="42e0c-117">Aby dodać siatkę właściwości ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="42e0c-117">To add a user setting property grid</span></span>  
  
1. <span data-ttu-id="42e0c-118">Dodaj formant **PropertyGrid** z **przybornika** do powierzchni projektowej `Form1`aplikacji, zakłada się, że w tym miejscu .</span><span class="sxs-lookup"><span data-stu-id="42e0c-118">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="42e0c-119">Domyślną nazwą formantu właściwości-siatki jest `PropertyGrid1`.</span><span class="sxs-lookup"><span data-stu-id="42e0c-119">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2. <span data-ttu-id="42e0c-120">Kliknij dwukrotnie powierzchnię `Form1` projektową, aby otworzyć kod programu obsługi zdarzeń ładowania formularza.</span><span class="sxs-lookup"><span data-stu-id="42e0c-120">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3. <span data-ttu-id="42e0c-121">Ustaw `My.Settings` obiekt jako zaznaczony obiekt dla siatki właściwości.</span><span class="sxs-lookup"><span data-stu-id="42e0c-121">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. <span data-ttu-id="42e0c-122">Skonfiguruj siatkę właściwości, aby wyświetlała tylko ustawienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="42e0c-122">Configure the property grid to show only the user settings.</span></span>  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > <span data-ttu-id="42e0c-123">Aby wyświetlić tylko ustawienia zakresu <xref:System.Configuration.ApplicationScopedSettingAttribute> aplikacji, użyj <xref:System.Configuration.UserScopedSettingAttribute>atrybutu zamiast .</span><span class="sxs-lookup"><span data-stu-id="42e0c-123">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="42e0c-124">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="42e0c-124">Robust Programming</span></span>  

 <span data-ttu-id="42e0c-125">Aplikacja zapisuje ustawienia użytkownika po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="42e0c-125">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="42e0c-126">Aby natychmiast zapisać ustawienia, `My.Settings.Save` należy wywołać metodę.</span><span class="sxs-lookup"><span data-stu-id="42e0c-126">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="42e0c-127">Aby uzyskać więcej informacji, zobacz [Jak: Utrwalanie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="42e0c-127">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42e0c-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42e0c-128">See also</span></span>

- [<span data-ttu-id="42e0c-129">My.Settings, obiekt</span><span class="sxs-lookup"><span data-stu-id="42e0c-129">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="42e0c-130">Porady: odczytywanie ustawień aplikacji w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42e0c-130">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="42e0c-131">Porady: zmienianie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42e0c-131">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="42e0c-132">Porady: utrwalanie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42e0c-132">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="42e0c-133">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="42e0c-133">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
