---
title: 'Instrukcje: Tworzenie ustawień aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], creating
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
ms.openlocfilehash: a6b63e5e48e64491e5f33e7aec4abf92ccf48708
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166403"
---
# <a name="how-to-create-application-settings"></a><span data-ttu-id="af9c5-102">Instrukcje: Tworzenie ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="af9c5-102">How to: Create Application Settings</span></span>
<span data-ttu-id="af9c5-103">Przy użyciu kodu zarządzanego, można tworzyć nowych ustawień aplikacji i wiązania ich z właściwościami w formularzu lub kontrolki formularza tak, aby te ustawienia są ładowane i zapisywane automatycznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="af9c5-103">Using managed code, you can create new application settings and bind them to properties on your form or your form's controls, so that these settings are loaded and saved automatically at run time.</span></span>  
  
 <span data-ttu-id="af9c5-104">W poniższej procedurze należy ręcznie utworzyć klasy otoki, która pochodzi od klasy <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="af9c5-104">In the following procedure, you manually create a wrapper class that derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span> <span data-ttu-id="af9c5-105">Aby tej klasy należy dodać publicznie dostępnych właściwości dla każdego ustawienia aplikacji, które chcesz udostępnić.</span><span class="sxs-lookup"><span data-stu-id="af9c5-105">To this class you add a publicly accessible property for each application setting that you want to expose.</span></span>  
  
 <span data-ttu-id="af9c5-106">Można również wykonać tę procedurę za pomocą minimalnej ilości kodu w Projektancie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="af9c5-106">You can also perform this procedure using minimal code in the Visual Studio designer.</span></span>  <span data-ttu-id="af9c5-107">Zobacz też [jak: Tworzenie ustawień aplikacji za pomocą projektanta](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/wabtadw6(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="af9c5-107">Also see [How to: Create Application Settings Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/wabtadw6(v=vs.100)).</span></span>  
  
### <a name="to-create-new-application-settings-programmatically"></a><span data-ttu-id="af9c5-108">Aby programowo utworzyć nowe ustawienia aplikacji</span><span class="sxs-lookup"><span data-stu-id="af9c5-108">To create new Application Settings programmatically</span></span>  
  
1.  <span data-ttu-id="af9c5-109">Dodaj nową klasę do projektu i zmień jego nazwę.</span><span class="sxs-lookup"><span data-stu-id="af9c5-109">Add a new class to your project, and rename it.</span></span> <span data-ttu-id="af9c5-110">Do wykonania tej procedury, firma Microsoft będzie wywoływać tej klasy `MyUserSettings`.</span><span class="sxs-lookup"><span data-stu-id="af9c5-110">For this procedure, we will call this class `MyUserSettings`.</span></span> <span data-ttu-id="af9c5-111">Zmiana definicji klasy, aby klasa pochodzi od klasy <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="af9c5-111">Change the class definition so that the class derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span>  
  
2.  <span data-ttu-id="af9c5-112">Zdefiniuj właściwość od tej klasy otoki dla każdego ustawienia aplikacji, potrzebujesz, a następnie Zastosuj tę właściwość z oboma <xref:System.Configuration.ApplicationScopedSettingAttribute> lub <xref:System.Configuration.UserScopedSettingAttribute>, w zależności od zakresu ustawienia.</span><span class="sxs-lookup"><span data-stu-id="af9c5-112">Define a property on this wrapper class for each application setting you require, and apply that property with either the <xref:System.Configuration.ApplicationScopedSettingAttribute> or <xref:System.Configuration.UserScopedSettingAttribute>, depending on the scope of the setting.</span></span> <span data-ttu-id="af9c5-113">Aby uzyskać więcej informacji na temat zakresu ustawień, zobacz [Przegląd ustawień aplikacji](application-settings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="af9c5-113">For more information about settings scope, see [Application Settings Overview](application-settings-overview.md).</span></span> <span data-ttu-id="af9c5-114">W razie kod powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="af9c5-114">By now, your code should look like this:</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3.  <span data-ttu-id="af9c5-115">W aplikacji, należy utworzyć wystąpienie tej klasy otoki.</span><span class="sxs-lookup"><span data-stu-id="af9c5-115">Create an instance of this wrapper class in your application.</span></span> <span data-ttu-id="af9c5-116">Będzie najczęściej od prywatnej składowej formularza głównego.</span><span class="sxs-lookup"><span data-stu-id="af9c5-116">It will commonly be a private member of the main form.</span></span> <span data-ttu-id="af9c5-117">Po zdefiniowaniu klasy należy powiązać go z właściwością; w tym przypadku <xref:System.Windows.Forms.Form.BackColor%2A> właściwości formularza.</span><span class="sxs-lookup"><span data-stu-id="af9c5-117">Now that you have defined your class, you need to bind it to a property; in this case, the <xref:System.Windows.Forms.Form.BackColor%2A> property of your form.</span></span> <span data-ttu-id="af9c5-118">Można to zrobić do formularza `Load` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af9c5-118">You can accomplish this in your form's `Load` event handler.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="af9c5-119">Jeśli podasz sposób, aby zmienić ustawienia w czasie wykonywania, należy zapisać bieżące ustawienia użytkownika na dysku w przypadku, gdy formularz zostanie zamknięty, w przeciwnym razie te zmiany zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="af9c5-119">If you provide a way to change settings at run time, you will need to save the user's current settings to disk when your form closes, or else these changes will be lost.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#3](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     <span data-ttu-id="af9c5-120">Możesz pomyślnie utworzono nowe ustawienie aplikacji i powiązany określonej właściwości.</span><span class="sxs-lookup"><span data-stu-id="af9c5-120">You have now successfully created a new application setting and bound it to the specified property.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="af9c5-121">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="af9c5-121">.NET Framework Security</span></span>  
 <span data-ttu-id="af9c5-122">Domyślny dostawca ustawień <xref:System.Configuration.LocalFileSettingsProvider>, będzie nadal występował, informacje w plikach konfiguracji jako zwykły tekst.</span><span class="sxs-lookup"><span data-stu-id="af9c5-122">The default settings provider, <xref:System.Configuration.LocalFileSettingsProvider>, persists information to configuration files as plain text.</span></span> <span data-ttu-id="af9c5-123">Ogranicza to zabezpieczeń w celu zabezpieczenia dostępu do plików, które są dostarczane przez system operacyjny dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="af9c5-123">This limits security to the file access security provided by the operating system for the current user.</span></span> <span data-ttu-id="af9c5-124">W związku z tym należy uważać, z informacjami przechowywanymi w plikach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="af9c5-124">Because of this, care must be taken with the information stored in configuration files.</span></span> <span data-ttu-id="af9c5-125">Na przykład jeden typowym celem zastosowania ustawienia aplikacji jest przechowywanie parametrów połączenia, prowadzące do aplikacji w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="af9c5-125">For example, one common use for application settings is to store connection strings that point to the application's data store.</span></span> <span data-ttu-id="af9c5-126">Jednak ze względu na problemy dotyczące zabezpieczeń, takich ciągów nie może zawierać hasła.</span><span class="sxs-lookup"><span data-stu-id="af9c5-126">However, because of security concerns, such strings should not include passwords.</span></span> <span data-ttu-id="af9c5-127">Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz <xref:System.Configuration.SpecialSetting>.</span><span class="sxs-lookup"><span data-stu-id="af9c5-127">For more information about connection strings, see <xref:System.Configuration.SpecialSetting>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af9c5-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af9c5-128">See also</span></span>

- <xref:System.Configuration.SpecialSettingAttribute>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [<span data-ttu-id="af9c5-129">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="af9c5-129">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="af9c5-130">Instrukcje: Walidacja ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="af9c5-130">How to: Validate Application Settings</span></span>](how-to-validate-application-settings.md)
