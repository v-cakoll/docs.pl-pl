---
title: 'Porady: tworzenie nowego ustawienia w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: 618355948578bd8f15e8cf7bec6f599e3169b77a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523770"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="c5a1d-102">Porady: tworzenie nowego ustawienia w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="c5a1d-102">How To: Create a New Setting at Design Time</span></span>
<span data-ttu-id="c5a1d-103">Przy użyciu narzędzia Projektant ustawienia, można utworzyć nowe ustawienie w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-103">You can create a new setting at design time by using the Settings designer.</span></span> <span data-ttu-id="c5a1d-104">Projektant ustawienia jest interfejsem styl siatki, który pozwala utworzyć nowe ustawienia, a także określać właściwości dla tych ustawień.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="c5a1d-105">Należy określić nazwę, wartość, typ i zakres dla nowych ustawień.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="c5a1d-106">Po utworzeniu ustawienie jest dostępne w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-106">Once a setting is created, it is accessible in code.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="c5a1d-107">Aby utworzyć nowe ustawienie w czasie projektowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c5a1d-107">To create a new setting at design time in C#</span></span>  
  
1.  <span data-ttu-id="c5a1d-108">W **Eksploratora rozwiązań**, rozwiń węzeł **właściwości** węzła projektu.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-108">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>  
  
2.  <span data-ttu-id="c5a1d-109">Kliknij dwukrotnie plik .settings, w której chcesz dodać nowe ustawienie.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-109">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="c5a1d-110">Domyślna nazwa pliku to Settings.settings.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-110">The default name for this file is Settings.settings.</span></span>  
  
3.  <span data-ttu-id="c5a1d-111">W ustawieniach projektanta, ustaw nazwę, wartość, typ i zakres dla ustawienia.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-111">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="c5a1d-112">Każdy wiersz reprezentuje ustawienia jednej.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-112">Each row represents a single setting.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="c5a1d-113">Aby utworzyć nowe ustawienie w czasie projektowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c5a1d-113">To create a new setting at design time in Visual Basic</span></span>  
  
1.  <span data-ttu-id="c5a1d-114">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-114">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="c5a1d-115">W **właściwości** wybierz pozycję **ustawienia** kartę.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-115">In the **Properties** page, select the **Settings** tab.</span></span>  
  
3.  <span data-ttu-id="c5a1d-116">W ustawieniach projektanta, ustaw nazwę, wartość, typ i zakres dla ustawienia.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-116">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="c5a1d-117">Każdy wiersz reprezentuje ustawienia jednej.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-117">Each row represents a single setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5a1d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5a1d-118">See Also</span></span>  
 [<span data-ttu-id="c5a1d-119">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="c5a1d-119">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="c5a1d-120">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="c5a1d-120">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [<span data-ttu-id="c5a1d-121">Instrukcje: zmiana wartości istniejącego ustawienia w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="c5a1d-121">How To: Change the Value of an Existing Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)
