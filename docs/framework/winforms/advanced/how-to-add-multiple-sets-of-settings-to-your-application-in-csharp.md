---
title: "Porady: dodawanie wielu zestawów ustawień do aplikacji w C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d9bd7d0721aae8691fdbca4d7b934f820666536
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="8d034-102">Porady: dodawanie wielu zestawów ustawień do aplikacji w C#</span><span class="sxs-lookup"><span data-stu-id="8d034-102">How To: Add Multiple Sets of Settings To Your Application in C#</span></span> #
<span data-ttu-id="8d034-103">W niektórych przypadkach można mieć wielu zestawów ustawień w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8d034-103">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="8d034-104">Na przykład jeśli tworzysz aplikację, których można oczekiwać określonej grupy ustawień można zmienić często, można ją rozsądnego je rozdzielić wszystko w jednym pliku, dzięki czemu plik można zastąpić hurtowym, pozostawiając inne ustawienia nie mają wpływu.</span><span class="sxs-lookup"><span data-stu-id="8d034-104">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="8d034-105">Program Visual Studio umożliwia dodawanie wielu zestawów ustawień do projektu.</span><span class="sxs-lookup"><span data-stu-id="8d034-105">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="8d034-106">Ustawia dodatkowe ustawienia są dostępne za pośrednictwem obiektu Properties.Settings.</span><span class="sxs-lookup"><span data-stu-id="8d034-106">Additional sets of settings can be accessed via the Properties.Settings object.</span></span>  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a><span data-ttu-id="8d034-107">Aby dodać dodatkowy zestaw ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="8d034-107">To Add an Additional Set of Setting to your Application</span></span>  
  
1.  <span data-ttu-id="8d034-108">Z **projektu** menu, wybierz **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="8d034-108">From the **Project** menu, choose **Add New Item**.</span></span> <span data-ttu-id="8d034-109">**Dodaj nowy element** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="8d034-109">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="8d034-110">W **Dodaj nowy element** okno dialogowe, wybierz opcję **pliku ustawień**, wpisz nazwę pliku i kliknij przycisk **Dodaj** można dodać nowego pliku ustawień do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="8d034-110">In the **Add New Item** dialog box, select **Settings File**, type in a name for the file, and click **Add** to add a new settings file to your solution.</span></span>  
  
3.  <span data-ttu-id="8d034-111">W **Eksploratora rozwiązań**, przeciągnij nowy plik ustawień do **właściwości** folderu.</span><span class="sxs-lookup"><span data-stu-id="8d034-111">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="8d034-112">Dzięki temu nowe ustawienia mają być dostępne w kodzie.</span><span class="sxs-lookup"><span data-stu-id="8d034-112">This allows your new settings to be available in code.</span></span>  
  
4.  <span data-ttu-id="8d034-113">Dodaj i użyj ustawień w tym pliku, jak w przypadku każdego innego pliku ustawień.</span><span class="sxs-lookup"><span data-stu-id="8d034-113">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="8d034-114">Ta grupa ustawień za pomocą obiektu Properties.Settings są dostępne.</span><span class="sxs-lookup"><span data-stu-id="8d034-114">You can access this group of settings via the Properties.Settings object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d034-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d034-115">See Also</span></span>  
 [<span data-ttu-id="8d034-116">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="8d034-116">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="8d034-117">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="8d034-117">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
