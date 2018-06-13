---
title: 'Porady: dodawanie wielu zestawów ustawień do aplikacji w C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 029dffc878c62613e291620a2bd86971f369d15a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520812"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="9bf5d-102">Porady: dodawanie wielu zestawów ustawień do aplikacji w C#</span><span class="sxs-lookup"><span data-stu-id="9bf5d-102">How To: Add Multiple Sets of Settings To Your Application in C#</span></span> #
<span data-ttu-id="9bf5d-103">W niektórych przypadkach można mieć wielu zestawów ustawień w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9bf5d-103">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="9bf5d-104">Na przykład jeśli tworzysz aplikację, których można oczekiwać określonej grupy ustawień można zmienić często, można ją rozsądnego je rozdzielić wszystko w jednym pliku, dzięki czemu plik można zastąpić hurtowym, pozostawiając inne ustawienia nie mają wpływu.</span><span class="sxs-lookup"><span data-stu-id="9bf5d-104">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="9bf5d-105">Program Visual Studio umożliwia dodawanie wielu zestawów ustawień do projektu.</span><span class="sxs-lookup"><span data-stu-id="9bf5d-105">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="9bf5d-106">Ustawia dodatkowe ustawienia są dostępne za pośrednictwem obiektu Properties.Settings.</span><span class="sxs-lookup"><span data-stu-id="9bf5d-106">Additional sets of settings can be accessed via the Properties.Settings object.</span></span>  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a><span data-ttu-id="9bf5d-107">Aby dodać dodatkowy zestaw ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="9bf5d-107">To Add an Additional Set of Setting to your Application</span></span>  
  
1.  <span data-ttu-id="9bf5d-108">Z **projektu** menu, wybierz **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="9bf5d-108">From the **Project** menu, choose **Add New Item**.</span></span> <span data-ttu-id="9bf5d-109">**Dodaj nowy element** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="9bf5d-109">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="9bf5d-110">W **Dodaj nowy element** okno dialogowe, wybierz opcję **pliku ustawień**, wpisz nazwę pliku i kliknij przycisk **Dodaj** można dodać nowego pliku ustawień do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9bf5d-110">In the **Add New Item** dialog box, select **Settings File**, type in a name for the file, and click **Add** to add a new settings file to your solution.</span></span>  
  
3.  <span data-ttu-id="9bf5d-111">W **Eksploratora rozwiązań**, przeciągnij nowy plik ustawień do **właściwości** folderu.</span><span class="sxs-lookup"><span data-stu-id="9bf5d-111">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="9bf5d-112">Dzięki temu nowe ustawienia mają być dostępne w kodzie.</span><span class="sxs-lookup"><span data-stu-id="9bf5d-112">This allows your new settings to be available in code.</span></span>  
  
4.  <span data-ttu-id="9bf5d-113">Dodaj i użyj ustawień w tym pliku, jak w przypadku każdego innego pliku ustawień.</span><span class="sxs-lookup"><span data-stu-id="9bf5d-113">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="9bf5d-114">Ta grupa ustawień za pomocą obiektu Properties.Settings są dostępne.</span><span class="sxs-lookup"><span data-stu-id="9bf5d-114">You can access this group of settings via the Properties.Settings object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bf5d-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9bf5d-115">See Also</span></span>  
 [<span data-ttu-id="9bf5d-116">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="9bf5d-116">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="9bf5d-117">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="9bf5d-117">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
