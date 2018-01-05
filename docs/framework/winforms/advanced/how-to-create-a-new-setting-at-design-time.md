---
title: 'Porady: tworzenie nowego ustawienia w czasie projektowania'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04b86579f45c5a357f8759bf36ae41f7a5c6e98b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="215b1-102">Porady: tworzenie nowego ustawienia w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="215b1-102">How To: Create a New Setting at Design Time</span></span>
<span data-ttu-id="215b1-103">Przy użyciu narzędzia Projektant ustawienia, można utworzyć nowe ustawienie w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="215b1-103">You can create a new setting at design time by using the Settings designer.</span></span> <span data-ttu-id="215b1-104">Projektant ustawienia jest interfejsem styl siatki, który pozwala utworzyć nowe ustawienia, a także określać właściwości dla tych ustawień.</span><span class="sxs-lookup"><span data-stu-id="215b1-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="215b1-105">Należy określić nazwę, wartość, typ i zakres dla nowych ustawień.</span><span class="sxs-lookup"><span data-stu-id="215b1-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="215b1-106">Po utworzeniu ustawienie jest dostępne w kodzie.</span><span class="sxs-lookup"><span data-stu-id="215b1-106">Once a setting is created, it is accessible in code.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="215b1-107">Aby utworzyć nowe ustawienie w czasie projektowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="215b1-107">To create a new setting at design time in C#</span></span>  
  
1.  <span data-ttu-id="215b1-108">W **Eksploratora rozwiązań**, rozwiń węzeł **właściwości** węzła projektu.</span><span class="sxs-lookup"><span data-stu-id="215b1-108">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>  
  
2.  <span data-ttu-id="215b1-109">Kliknij dwukrotnie plik .settings, w której chcesz dodać nowe ustawienie.</span><span class="sxs-lookup"><span data-stu-id="215b1-109">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="215b1-110">Domyślna nazwa pliku to Settings.settings.</span><span class="sxs-lookup"><span data-stu-id="215b1-110">The default name for this file is Settings.settings.</span></span>  
  
3.  <span data-ttu-id="215b1-111">W ustawieniach projektanta, ustaw nazwę, wartość, typ i zakres dla ustawienia.</span><span class="sxs-lookup"><span data-stu-id="215b1-111">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="215b1-112">Każdy wiersz reprezentuje ustawienia jednej.</span><span class="sxs-lookup"><span data-stu-id="215b1-112">Each row represents a single setting.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="215b1-113">Aby utworzyć nowe ustawienie w czasie projektowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="215b1-113">To create a new setting at design time in Visual Basic</span></span>  
  
1.  <span data-ttu-id="215b1-114">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="215b1-114">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="215b1-115">W **właściwości** wybierz pozycję **ustawienia** kartę.</span><span class="sxs-lookup"><span data-stu-id="215b1-115">In the **Properties** page, select the **Settings** tab.</span></span>  
  
3.  <span data-ttu-id="215b1-116">W ustawieniach projektanta, ustaw nazwę, wartość, typ i zakres dla ustawienia.</span><span class="sxs-lookup"><span data-stu-id="215b1-116">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="215b1-117">Każdy wiersz reprezentuje ustawienia jednej.</span><span class="sxs-lookup"><span data-stu-id="215b1-117">Each row represents a single setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="215b1-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="215b1-118">See Also</span></span>  
 [<span data-ttu-id="215b1-119">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="215b1-119">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="215b1-120">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="215b1-120">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [<span data-ttu-id="215b1-121">Instrukcje: zmiana wartości istniejącego ustawienia w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="215b1-121">How To: Change the Value of an Existing Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)
