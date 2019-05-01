---
title: 'Instrukcje: Tworzenie nowego ustawienia w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: e371c60e3fb674e4243cec008e1098172725d4cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937725"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="171e1-102">Instrukcje: Tworzenie nowego ustawienia w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="171e1-102">How To: Create a New Setting at Design Time</span></span>
<span data-ttu-id="171e1-103">Za pomocą projektanta ustawień, można utworzyć nowe ustawienie w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="171e1-103">You can create a new setting at design time by using the Settings designer.</span></span> <span data-ttu-id="171e1-104">Projektant ustawień jest interfejsem styl siatki, która pozwala na tworzenie nowych ustawień, a następnie określ właściwości tych ustawień.</span><span class="sxs-lookup"><span data-stu-id="171e1-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="171e1-105">Należy określić nazwę, wartość, typie i zakresie dla nowych ustawień.</span><span class="sxs-lookup"><span data-stu-id="171e1-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="171e1-106">Po utworzeniu to ustawienie jest dostępne w kodzie.</span><span class="sxs-lookup"><span data-stu-id="171e1-106">Once a setting is created, it is accessible in code.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="171e1-107">Aby utworzyć nowe ustawienie w czasie projektowania w języku C\#</span><span class="sxs-lookup"><span data-stu-id="171e1-107">To create a new setting at design time in C\#</span></span>
  
1. <span data-ttu-id="171e1-108">W **Eksploratora rozwiązań**, rozwiń węzeł **właściwości** węzła projektu.</span><span class="sxs-lookup"><span data-stu-id="171e1-108">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>  
  
2. <span data-ttu-id="171e1-109">Kliknij dwukrotnie plik .settings, w której chcesz dodać nowe ustawienie.</span><span class="sxs-lookup"><span data-stu-id="171e1-109">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="171e1-110">Domyślna nazwa dla tego pliku jest Settings.settings.</span><span class="sxs-lookup"><span data-stu-id="171e1-110">The default name for this file is Settings.settings.</span></span>  
  
3. <span data-ttu-id="171e1-111">W Projektancie ustawień Ustaw nazwę, wartość, typie i zakresie dla ustawienia.</span><span class="sxs-lookup"><span data-stu-id="171e1-111">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="171e1-112">Każdy wiersz reprezentuje ustawienia jednej.</span><span class="sxs-lookup"><span data-stu-id="171e1-112">Each row represents a single setting.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="171e1-113">Aby utworzyć nowe ustawienie w czasie projektowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="171e1-113">To create a new setting at design time in Visual Basic</span></span>  
  
1. <span data-ttu-id="171e1-114">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="171e1-114">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>  
  
2. <span data-ttu-id="171e1-115">W **właściwości** wybierz opcję **ustawienia** kartę.</span><span class="sxs-lookup"><span data-stu-id="171e1-115">In the **Properties** page, select the **Settings** tab.</span></span>  
  
3. <span data-ttu-id="171e1-116">W Projektancie ustawień Ustaw nazwę, wartość, typie i zakresie dla ustawienia.</span><span class="sxs-lookup"><span data-stu-id="171e1-116">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="171e1-117">Każdy wiersz reprezentuje ustawienia jednej.</span><span class="sxs-lookup"><span data-stu-id="171e1-117">Each row represents a single setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="171e1-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="171e1-118">See also</span></span>

- [<span data-ttu-id="171e1-119">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="171e1-119">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="171e1-120">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="171e1-120">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="171e1-121">Instrukcje: Zmiana wartości istniejącego ustawienia w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="171e1-121">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
