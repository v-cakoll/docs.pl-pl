---
title: 'Instrukcje: Dodawanie wielu zestawów ustawień do aplikacji w C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 106e0ee0b8775f329f3ffd8babe458cac8492bd5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187385"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="86c6f-102">Instrukcje: Dodawanie wielu zestawów ustawień do aplikacji w języku C\#</span><span class="sxs-lookup"><span data-stu-id="86c6f-102">How To: Add Multiple Sets of Settings To Your Application in C\#</span></span>
<span data-ttu-id="86c6f-103">W niektórych przypadkach możesz chcieć mieć wielu zestawów ustawień w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="86c6f-103">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="86c6f-104">Na przykład jeśli tworzysz aplikację, której dana grupa ustawień oczekuje się, zmieniają się często, może być poddanie oddzielić je wszystkie w jednym pliku, dzięki czemu plik można zastąpić hurtowym, pozostawiając inne ustawienia bez zmian.</span><span class="sxs-lookup"><span data-stu-id="86c6f-104">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="86c6f-105">Program Visual Studio umożliwia dodawanie wielu zestawów ustawień do projektu.</span><span class="sxs-lookup"><span data-stu-id="86c6f-105">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="86c6f-106">Dodatkowe zestawy ustawienia są dostępne za pośrednictwem obiektu Properties.Settings.</span><span class="sxs-lookup"><span data-stu-id="86c6f-106">Additional sets of settings can be accessed via the Properties.Settings object.</span></span>  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a><span data-ttu-id="86c6f-107">Aby dodać dodatkowy zestaw ustawień do aplikacji</span><span class="sxs-lookup"><span data-stu-id="86c6f-107">To Add an Additional Set of Setting to your Application</span></span>  
  
1.  <span data-ttu-id="86c6f-108">Z **projektu** menu, wybierz **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="86c6f-108">From the **Project** menu, choose **Add New Item**.</span></span> <span data-ttu-id="86c6f-109">**Dodaj nowy element** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="86c6f-109">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="86c6f-110">W **Dodaj nowy element** okno dialogowe, wybierz opcję **pliku ustawień**, wpisz nazwę pliku, a kliknij **Dodaj** Aby dodać nowy plik ustawień do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="86c6f-110">In the **Add New Item** dialog box, select **Settings File**, type in a name for the file, and click **Add** to add a new settings file to your solution.</span></span>  
  
3.  <span data-ttu-id="86c6f-111">W **Eksploratora rozwiązań**, przeciągnij nowy plik ustawień do **właściwości** folderu.</span><span class="sxs-lookup"><span data-stu-id="86c6f-111">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="86c6f-112">Dzięki temu nowe ustawienia będą dostępne w kodzie.</span><span class="sxs-lookup"><span data-stu-id="86c6f-112">This allows your new settings to be available in code.</span></span>  
  
4.  <span data-ttu-id="86c6f-113">Dodaj, a następnie użyj ustawień w tym pliku, tak jak każdy inny plik ustawień.</span><span class="sxs-lookup"><span data-stu-id="86c6f-113">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="86c6f-114">Ta grupa ustawień za pomocą obiektu Properties.Settings możesz uzyskać dostęp.</span><span class="sxs-lookup"><span data-stu-id="86c6f-114">You can access this group of settings via the Properties.Settings object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c6f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86c6f-115">See also</span></span>

- [<span data-ttu-id="86c6f-116">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="86c6f-116">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="86c6f-117">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="86c6f-117">Application Settings Overview</span></span>](application-settings-overview.md)
