---
title: 'Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: 5f4b962762aeecea65748c5456bc4a2d75595d4f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311620"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="c5e35-102">Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c5e35-102">How to: Create Property Grids for User Settings in Visual Basic</span></span>
<span data-ttu-id="c5e35-103">Można utworzyć siatki właściwości, dla ustawień użytkownika, definiując <xref:System.Windows.Forms.PropertyGrid> kontrola przy użyciu właściwości ustawienia użytkownika `My.Settings` obiektu.</span><span class="sxs-lookup"><span data-stu-id="c5e35-103">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5e35-104">W kolejności, w tym przykładzie do pracy aplikacja musi mieć jej ustawienia użytkownika skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="c5e35-104">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="c5e35-105">Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="c5e35-105">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="c5e35-106">`My.Settings` Obiekt udostępnia każdego ustawienia jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="c5e35-106">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="c5e35-107">Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taka sama jak typ ustawienia.</span><span class="sxs-lookup"><span data-stu-id="c5e35-107">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="c5e35-108">Ustawienie **zakres** Określa, czy właściwość jest tylko do odczytu; właściwość dla **aplikacji**— ustawienie zakresu jest tylko do odczytu, podczas właściwość dla **użytkownika**-zakresu Ustawienie to odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="c5e35-108">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="c5e35-109">Aby uzyskać więcej informacji, zobacz [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="c5e35-109">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5e35-110">Nie można zmienić ani zapisać wartości ustawień zakresu aplikacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c5e35-110">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="c5e35-111">Ustawienia zakresu aplikacji można zmienić tylko wtedy, gdy tworzenie aplikacji (za pośrednictwem **projektanta projektu**) lub przez edycję pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c5e35-111">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="c5e35-112">Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="c5e35-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="c5e35-113">W tym przykładzie użyto <xref:System.Windows.Forms.PropertyGrid> formantu, aby uzyskać dostęp do właściwości ustawienia użytkownika `My.Settings` obiektu.</span><span class="sxs-lookup"><span data-stu-id="c5e35-113">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="c5e35-114">Domyślnie <xref:System.Windows.Forms.PropertyGrid> pokazuje wszystkie właściwości `My.Settings` obiektu.</span><span class="sxs-lookup"><span data-stu-id="c5e35-114">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="c5e35-115">Jednak właściwości ustawienia użytkownika mają <xref:System.Configuration.UserScopedSettingAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c5e35-115">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="c5e35-116">W tym przykładzie <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> właściwość <xref:System.Windows.Forms.PropertyGrid> do <xref:System.Configuration.UserScopedSettingAttribute> Aby wyświetlić jej właściwości ustawień użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c5e35-116">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="c5e35-117">Aby dodać siatką właściwości ustawienia użytkownika</span><span class="sxs-lookup"><span data-stu-id="c5e35-117">To add a user setting property grid</span></span>  
  
1. <span data-ttu-id="c5e35-118">Dodaj **PropertyGrid** z kontrolować **przybornika** do powierzchni projektu dla aplikacji, w tym miejscu zakłada się, że `Form1`.</span><span class="sxs-lookup"><span data-stu-id="c5e35-118">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="c5e35-119">Domyślną nazwą formantu siatki właściwości jest `PropertyGrid1`.</span><span class="sxs-lookup"><span data-stu-id="c5e35-119">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2. <span data-ttu-id="c5e35-120">Kliknij dwukrotnie powierzchni projektowej dla `Form1` aby otworzyć kod obsługi zdarzeń formularz ładowanie.</span><span class="sxs-lookup"><span data-stu-id="c5e35-120">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3. <span data-ttu-id="c5e35-121">Ustaw `My.Settings` obiektu jako wybranego obiektu siatki właściwości.</span><span class="sxs-lookup"><span data-stu-id="c5e35-121">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. <span data-ttu-id="c5e35-122">Skonfiguruj siatki właściwości, aby pokazać tylko ustawienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c5e35-122">Configure the property grid to show only the user settings.</span></span>  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    >  <span data-ttu-id="c5e35-123">Wyświetlanie tylko ustawień zakresu aplikacji, należy użyć <xref:System.Configuration.ApplicationScopedSettingAttribute> atrybutu zamiast <xref:System.Configuration.UserScopedSettingAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c5e35-123">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c5e35-124">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="c5e35-124">Robust Programming</span></span>  
 <span data-ttu-id="c5e35-125">Aplikacja ustawienia użytkownika są zapisywane podczas zamykania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c5e35-125">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="c5e35-126">Aby zapisać ustawienia natychmiast, należy wywołać `My.Settings.Save` metody.</span><span class="sxs-lookup"><span data-stu-id="c5e35-126">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="c5e35-127">Aby uzyskać więcej informacji, zobacz [jak: Utrwalanie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="c5e35-127">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5e35-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5e35-128">See also</span></span>

- [<span data-ttu-id="c5e35-129">My.Settings, obiekt</span><span class="sxs-lookup"><span data-stu-id="c5e35-129">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="c5e35-130">Instrukcje: Odczytywanie ustawień aplikacji w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c5e35-130">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="c5e35-131">Instrukcje: Zmienianie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c5e35-131">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="c5e35-132">Instrukcje: Utrwalanie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c5e35-132">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="c5e35-133">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="c5e35-133">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
