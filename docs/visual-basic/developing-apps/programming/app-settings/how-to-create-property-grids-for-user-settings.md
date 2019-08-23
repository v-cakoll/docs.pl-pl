---
title: 'Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: 4a31b44cca61caea5fdf725405646f628b5430b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968394"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="5fdf0-102">Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5fdf0-102">How to: Create Property Grids for User Settings in Visual Basic</span></span>
<span data-ttu-id="5fdf0-103">Można utworzyć siatkę właściwości dla ustawień użytkownika, wypełniając <xref:System.Windows.Forms.PropertyGrid> kontrolkę właściwościami `My.Settings` ustawienia użytkownika obiektu.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-103">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5fdf0-104">Aby ten przykład działał, aplikacja musi mieć skonfigurowane ustawienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-104">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="5fdf0-105">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="5fdf0-105">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="5fdf0-106">`My.Settings` Obiekt uwidacznia każde ustawienie jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-106">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="5fdf0-107">Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taki sam jak typ ustawienia.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-107">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="5fdf0-108">**Zakres** ustawienia określa, czy właściwość jest tylko do odczytu; Właściwość dla ustawienia zakresu **aplikacji**jest tylko do odczytu, podczas gdy właściwość dla ustawienia zakresu **użytkownika**ma wartość odczyt i zapis.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-108">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="5fdf0-109">Aby uzyskać więcej informacji, zobacz [My. Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="5fdf0-109">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5fdf0-110">Nie można zmienić ani zapisać wartości ustawień zakresu aplikacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-110">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="5fdf0-111">Ustawienia zakresu aplikacji można zmienić tylko podczas tworzenia aplikacji (za pomocą **projektanta projektu**) lub edytując plik konfiguracyjny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-111">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="5fdf0-112">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="5fdf0-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="5fdf0-113">Ten przykład używa <xref:System.Windows.Forms.PropertyGrid> formantu, aby uzyskać dostęp do właściwości `My.Settings` ustawień użytkownika obiektu.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-113">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="5fdf0-114">Domyślnie program <xref:System.Windows.Forms.PropertyGrid> wyświetla wszystkie właściwości `My.Settings` obiektu.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-114">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="5fdf0-115">Jednak właściwości ustawienia użytkownika mają <xref:System.Configuration.UserScopedSettingAttribute> atrybut.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-115">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="5fdf0-116">Ten przykład ustawia <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> właściwość na <xref:System.Configuration.UserScopedSettingAttribute> , <xref:System.Windows.Forms.PropertyGrid> aby wyświetlić tylko właściwości ustawienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-116">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="5fdf0-117">Aby dodać siatkę właściwości ustawienia użytkownika</span><span class="sxs-lookup"><span data-stu-id="5fdf0-117">To add a user setting property grid</span></span>  
  
1. <span data-ttu-id="5fdf0-118">Dodaj kontrolkę **PropertyGrid** z **przybornika** do powierzchni projektowej aplikacji, założono, że jest to możliwe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-118">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="5fdf0-119">Domyślną nazwą kontrolki siatki właściwości jest `PropertyGrid1`.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-119">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2. <span data-ttu-id="5fdf0-120">Kliknij dwukrotnie powierzchnię `Form1` projektową, aby otworzyć kod dla programu obsługi zdarzeń w formie załadowanej.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-120">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3. <span data-ttu-id="5fdf0-121">`My.Settings` Ustaw obiekt jako wybrany obiekt dla siatki właściwości.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-121">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. <span data-ttu-id="5fdf0-122">Skonfiguruj siatkę właściwości w taki sposób, aby były wyświetlane tylko ustawienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-122">Configure the property grid to show only the user settings.</span></span>  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > <span data-ttu-id="5fdf0-123">Aby wyświetlić tylko ustawienia zakresu aplikacji, należy użyć <xref:System.Configuration.ApplicationScopedSettingAttribute> atrybutu <xref:System.Configuration.UserScopedSettingAttribute>zamiast.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-123">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5fdf0-124">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="5fdf0-124">Robust Programming</span></span>  
 <span data-ttu-id="5fdf0-125">Aplikacja zapisuje ustawienia użytkownika po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-125">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="5fdf0-126">Aby natychmiast zapisać ustawienia, wywołaj `My.Settings.Save` metodę.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-126">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="5fdf0-127">Aby uzyskać więcej informacji, zobacz [jak: Utrwalaj ustawienia użytkownika w](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5fdf0-127">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fdf0-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5fdf0-128">See also</span></span>

- [<span data-ttu-id="5fdf0-129">My.Settings, obiekt</span><span class="sxs-lookup"><span data-stu-id="5fdf0-129">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="5fdf0-130">Instrukcje: Odczytaj ustawienia aplikacji w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5fdf0-130">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="5fdf0-131">Instrukcje: Zmień ustawienia użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5fdf0-131">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="5fdf0-132">Instrukcje: Utrwalanie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5fdf0-132">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="5fdf0-133">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="5fdf0-133">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
