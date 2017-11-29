---
title: "Ustawienia aplikacji dotyczące kontrolek niestandardowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f8292ac459a2943376229ef62466b0a772430dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="application-settings-for-custom-controls"></a><span data-ttu-id="413ae-102">Ustawienia aplikacji dotyczące kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="413ae-102">Application Settings for Custom Controls</span></span>
<span data-ttu-id="413ae-103">Należy wykonać pewne zadania, aby zapewnić możliwość utrzymania ustawienia aplikacji, jeśli formanty są hostowane w aplikacjach innych firm Kontrolki niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="413ae-103">You must complete certain tasks to give your custom controls the ability to persist application settings when the controls are hosted in third-party applications.</span></span>  
  
 <span data-ttu-id="413ae-104">Większość dokumentacji dotyczące funkcji ustawienia aplikacji jest zapisywany przy założeniu, że tworzona aplikacja autonomiczna.</span><span class="sxs-lookup"><span data-stu-id="413ae-104">Most of the documentation about the Application Settings feature is written under the assumption that you are creating a standalone application.</span></span> <span data-ttu-id="413ae-105">Jednak w przypadku tworzenia formant, który będzie hostem inni deweloperzy w aplikacjach, należy wykonać kilka dodatkowych kroków formantu do utrwalenia jego ustawienia poprawnie.</span><span class="sxs-lookup"><span data-stu-id="413ae-105">However, if you are creating a control that other developers will host in their applications, you need to take a few additional steps for your control to persist its settings properly.</span></span>  
  
## <a name="application-settings-and-custom-controls"></a><span data-ttu-id="413ae-106">Ustawienia aplikacji i kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="413ae-106">Application Settings and Custom Controls</span></span>  
 <span data-ttu-id="413ae-107">Dla formantu prawidłowo utrwalić jego ustawienia, go Hermetyzowanie procesu przez utworzenie własnego dedykowanego aplikacjami klasy otoki ustawień, pochodzących z <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="413ae-107">For your control to properly persist its settings, it must encapsulate the process by creating its own dedicated applications settings wrapper class, derived from <xref:System.Configuration.ApplicationSettingsBase>.</span></span> <span data-ttu-id="413ae-108">Ponadto należy zaimplementować klasy głównym formantu <xref:System.Configuration.IPersistComponentSettings>.</span><span class="sxs-lookup"><span data-stu-id="413ae-108">Additionally, the main control class must implement the <xref:System.Configuration.IPersistComponentSettings>.</span></span> <span data-ttu-id="413ae-109">Interfejs zawiera wiele właściwości, jak również dwie metody <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> i <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>.</span><span class="sxs-lookup"><span data-stu-id="413ae-109">The interface contains several properties as well as two methods, <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> and <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>.</span></span> <span data-ttu-id="413ae-110">Po dodaniu formantu do formularza używającego **Projektant formularzy systemu Windows** w programie Visual Studio, formularze systemu Windows będzie wywoływać <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> automatycznie, gdy formant jest inicjowany; należy wywołać <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> samodzielnie w `Dispose` Metoda formantu.</span><span class="sxs-lookup"><span data-stu-id="413ae-110">If you add your control to a form using the **Windows Forms Designer** in Visual Studio, Windows Forms will call <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> automatically when the control is initialized; you must call <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> yourself in the `Dispose` method of your control.</span></span>  
  
 <span data-ttu-id="413ae-111">Ponadto należy zaimplementować następujące w kolejności dla ustawienia aplikacji w przypadku kontrolek niestandardowych do poprawnego działania w czasie projektowania środowisk takiego jak Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="413ae-111">In addition, you should implement the following in order for application settings for custom controls to work properly in design-time environments such as Visual Studio:</span></span>  
  
1.  <span data-ttu-id="413ae-112">Klasa ustawień niestandardowych aplikacji z konstruktora przyjmującego <xref:System.ComponentModel.IComponent> jako jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="413ae-112">A custom application settings class with a constructor that takes an <xref:System.ComponentModel.IComponent> as a single parameter.</span></span> <span data-ttu-id="413ae-113">Ta klasa umożliwia zapisywanie i ładowanie wszystkie ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="413ae-113">Use this class to save and load all of your application settings.</span></span> <span data-ttu-id="413ae-114">Podczas tworzenia nowego wystąpienia tej klasy należy przekazać formantu niestandardowego za pomocą konstruktora.</span><span class="sxs-lookup"><span data-stu-id="413ae-114">When you create a new instance of this class, pass your custom control using the constructor.</span></span>  
  
2.  <span data-ttu-id="413ae-115">Tworzenie tej klasy niestandardowe ustawienia po utworzeniu i umieszczane na formularzu, takie jak w postaci formantu <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="413ae-115">Create this custom settings class after the control has been created and placed on a form, such as in the form's <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
 <span data-ttu-id="413ae-116">Aby uzyskać instrukcje tworzenia klasy ustawień niestandardowych, zobacz [porady: Tworzenie ustawień aplikacji](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).</span><span class="sxs-lookup"><span data-stu-id="413ae-116">For instructions on creating a custom settings class, see [How to: Create Application Settings](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).</span></span>  
  
## <a name="settings-keys-and-shared-settings"></a><span data-ttu-id="413ae-117">Ustawienia kluczy i ustawienia udostępnione</span><span class="sxs-lookup"><span data-stu-id="413ae-117">Settings Keys and Shared Settings</span></span>  
 <span data-ttu-id="413ae-118">Niektóre formanty mogą być używane wielokrotnie w ramach tego samego formularza.</span><span class="sxs-lookup"><span data-stu-id="413ae-118">Some controls can be used multiple times within the same form.</span></span> <span data-ttu-id="413ae-119">W większości przypadków, można tych kontrolek można utrwalić własne poszczególnych ustawień.</span><span class="sxs-lookup"><span data-stu-id="413ae-119">Most of the time, you will want these controls to persist their own individual settings.</span></span> <span data-ttu-id="413ae-120">Z <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> właściwość <xref:System.Configuration.IPersistComponentSettings>, możesz podać unikatowy ciąg, który służy do odróżniania wielu wersji kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="413ae-120">With the <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> property on <xref:System.Configuration.IPersistComponentSettings>, you can supply a unique string that acts to disambiguate multiple versions of a control on a form.</span></span>  
  
 <span data-ttu-id="413ae-121">Najprostszym sposobem, aby zaimplementować <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> jest użycie <xref:System.Windows.Forms.Control.Name%2A> właściwości formantu <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="413ae-121">The simplest way to implement <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> is to use the <xref:System.Windows.Forms.Control.Name%2A> property of the control for the <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>.</span></span> <span data-ttu-id="413ae-122">Po załadowaniu lub Zapisz ustawienia kontroli przekazać wartość <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> do <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> właściwość <xref:System.Configuration.ApplicationSettingsBase> klasy.</span><span class="sxs-lookup"><span data-stu-id="413ae-122">When you load or save the control's settings, you pass the value of <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> on to the <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> property of the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span> <span data-ttu-id="413ae-123">Ustawienia aplikacji używa to unikatowy klucz, jeśli będzie się powtarzał ustawienia użytkownika do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="413ae-123">Application Settings uses this unique key when it persists the user's settings to XML.</span></span> <span data-ttu-id="413ae-124">Poniższy kod przedstawia przykład sposobu `<userSettings>` sekcji może wyszukać wystąpienia niestandardowego formantu o nazwie `CustomControl1` który zapisuje ustawienie dla jego `Text` właściwości.</span><span class="sxs-lookup"><span data-stu-id="413ae-124">The following code example shows how a `<userSettings>` section may look for an instance of a custom control named `CustomControl1` that saves a setting for its `Text` property.</span></span>  
  
```xml  
<userSettings>  
    <CustomControl1>  
        <setting name="Text" serializedAs="string">  
            <value>Hello, World</value>  
        </setting>  
    </CustomControl1>  
</userSettings>  
```  
  
 <span data-ttu-id="413ae-125">Wszystkie wystąpienia formantu, który nie zostanie podana wartość <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> będzie mają te same ustawienia.</span><span class="sxs-lookup"><span data-stu-id="413ae-125">Any instances of a control that do not supply a value for <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> will share the same settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="413ae-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="413ae-126">See Also</span></span>  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.IPersistComponentSettings>  
 [<span data-ttu-id="413ae-127">Architektura ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="413ae-127">Application Settings Architecture</span></span>](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)
