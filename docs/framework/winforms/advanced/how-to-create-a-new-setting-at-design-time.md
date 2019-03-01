---
title: 'Instrukcje: Utwórz nowe ustawienie w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: c936adb6d4d80032b862994c21178a505da6789b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964256"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="390d5-102">Instrukcje: Utwórz nowe ustawienie w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="390d5-102">How To: Create a New Setting at Design Time</span></span>
<span data-ttu-id="390d5-103">Za pomocą projektanta ustawień, można utworzyć nowe ustawienie w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="390d5-103">You can create a new setting at design time by using the Settings designer.</span></span> <span data-ttu-id="390d5-104">Projektant ustawień jest interfejsem styl siatki, która pozwala na tworzenie nowych ustawień, a następnie określ właściwości tych ustawień.</span><span class="sxs-lookup"><span data-stu-id="390d5-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="390d5-105">Należy określić nazwę, wartość, typie i zakresie dla nowych ustawień.</span><span class="sxs-lookup"><span data-stu-id="390d5-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="390d5-106">Po utworzeniu to ustawienie jest dostępne w kodzie.</span><span class="sxs-lookup"><span data-stu-id="390d5-106">Once a setting is created, it is accessible in code.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="390d5-107">Aby utworzyć nowe ustawienie w czasie projektowania w języku C\#</span><span class="sxs-lookup"><span data-stu-id="390d5-107">To create a new setting at design time in C\#</span></span>
  
1.  <span data-ttu-id="390d5-108">W **Eksploratora rozwiązań**, rozwiń węzeł **właściwości** węzła projektu.</span><span class="sxs-lookup"><span data-stu-id="390d5-108">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>  
  
2.  <span data-ttu-id="390d5-109">Kliknij dwukrotnie plik .settings, w której chcesz dodać nowe ustawienie.</span><span class="sxs-lookup"><span data-stu-id="390d5-109">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="390d5-110">Domyślna nazwa dla tego pliku jest Settings.settings.</span><span class="sxs-lookup"><span data-stu-id="390d5-110">The default name for this file is Settings.settings.</span></span>  
  
3.  <span data-ttu-id="390d5-111">W Projektancie ustawień Ustaw nazwę, wartość, typie i zakresie dla ustawienia.</span><span class="sxs-lookup"><span data-stu-id="390d5-111">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="390d5-112">Każdy wiersz reprezentuje ustawienia jednej.</span><span class="sxs-lookup"><span data-stu-id="390d5-112">Each row represents a single setting.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="390d5-113">Aby utworzyć nowe ustawienie w czasie projektowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="390d5-113">To create a new setting at design time in Visual Basic</span></span>  
  
1.  <span data-ttu-id="390d5-114">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="390d5-114">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="390d5-115">W **właściwości** wybierz opcję **ustawienia** kartę.</span><span class="sxs-lookup"><span data-stu-id="390d5-115">In the **Properties** page, select the **Settings** tab.</span></span>  
  
3.  <span data-ttu-id="390d5-116">W Projektancie ustawień Ustaw nazwę, wartość, typie i zakresie dla ustawienia.</span><span class="sxs-lookup"><span data-stu-id="390d5-116">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="390d5-117">Każdy wiersz reprezentuje ustawienia jednej.</span><span class="sxs-lookup"><span data-stu-id="390d5-117">Each row represents a single setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="390d5-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="390d5-118">See also</span></span>
- [<span data-ttu-id="390d5-119">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="390d5-119">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [<span data-ttu-id="390d5-120">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="390d5-120">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="390d5-121">Instrukcje: Zmiana wartości istniejącego ustawienia w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="390d5-121">How To: Change the Value of an Existing Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)
