---
title: "Porady: utrwalanie ustawień użytkownika w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e1cf424a4e587818a8e2766a5e27c084010c084c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="8f28c-102">Porady: utrwalanie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8f28c-102">How to: Persist User Settings in Visual Basic</span></span>
<span data-ttu-id="8f28c-103">Można użyć `My.Settings.Save` metody do utrwalania zmian ustawień użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8f28c-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="8f28c-104">Zazwyczaj aplikacje są zaprojektowane, aby utrwalić zmiany ustawień użytkownika podczas zamykania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8f28c-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="8f28c-105">Jest to spowodowane zapisywania ustawień może potrwać, w zależności od wielu czynników, kilka sekund.</span><span class="sxs-lookup"><span data-stu-id="8f28c-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="8f28c-106">Aby uzyskać więcej informacji, zobacz [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="8f28c-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f28c-107">Mimo że można zmienić i zapisać wartości ustawień w zakresie użytkownika w czasie wykonywania, ustawienia zakresu aplikacji są tylko do odczytu i nie można zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="8f28c-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="8f28c-108">Możesz zmienić ustawienia zakres aplikacji, podczas tworzenia aplikacji, za pomocą **projektanta projektu**, lub poprzez edycję pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8f28c-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="8f28c-109">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="8f28c-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f28c-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="8f28c-110">Example</span></span>  
 <span data-ttu-id="8f28c-111">W tym przykładzie zmienia wartość `LastChanged` ustawienia użytkownika i zapisuje, które zmiany wywołując `My.Settings.Save` metody.</span><span class="sxs-lookup"><span data-stu-id="8f28c-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-persist-user-settings_1.vb)]  
  
 <span data-ttu-id="8f28c-112">W tym przykładzie działała, aplikacja musi mieć `LastChanged` ustawienia użytkownika, typu `Date`.</span><span class="sxs-lookup"><span data-stu-id="8f28c-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="8f28c-113">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="8f28c-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f28c-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f28c-114">See Also</span></span>  
 [<span data-ttu-id="8f28c-115">My.Settings — obiekt</span><span class="sxs-lookup"><span data-stu-id="8f28c-115">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="8f28c-116">Porady: odczytywanie ustawień aplikacji w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8f28c-116">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [<span data-ttu-id="8f28c-117">Porady: Zmienianie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8f28c-117">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [<span data-ttu-id="8f28c-118">Porady: tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8f28c-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [<span data-ttu-id="8f28c-119">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="8f28c-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
