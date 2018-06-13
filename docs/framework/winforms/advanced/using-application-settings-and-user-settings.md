---
title: Używanie ustawień aplikacji i ustawień użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- user settings [Windows Forms]
- application settings [Windows Forms], how-to topics
ms.assetid: 54682d3b-1cbf-4683-9351-012b8b4286b5
ms.openlocfilehash: f5231ecc9fb3898d60241ea8a53b509daced8a0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523845"
---
# <a name="using-application-settings-and-user-settings"></a><span data-ttu-id="d3387-102">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="d3387-102">Using Application Settings and User Settings</span></span>
<span data-ttu-id="d3387-103">Począwszy od programu .NET Framework 2.0, można utworzyć i zapisać wartości, które są zachowywane między sesjami wykonywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d3387-103">Starting with the .NET Framework 2.0, you can create and access values that are persisted between application execution sessions.</span></span> <span data-ttu-id="d3387-104">Wartości te są nazywane *ustawienia*.</span><span class="sxs-lookup"><span data-stu-id="d3387-104">These values are called *settings*.</span></span> <span data-ttu-id="d3387-105">Ustawienia reprezentują preferencji użytkownika lub cenne informacje aplikacja powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="d3387-105">Settings can represent user preferences, or valuable information the application needs to use.</span></span> <span data-ttu-id="d3387-106">Na przykład utworzyć szereg ustawień, na których są przechowywane preferencje użytkownika dotyczące schemat kolorów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d3387-106">For example, you might create a series of settings that store user preferences for the color scheme of an application.</span></span> <span data-ttu-id="d3387-107">Lub może przechowywać parametry połączenia, które określa bazę danych używanych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="d3387-107">Or you might store the connection string that specifies a database that your application uses.</span></span> <span data-ttu-id="d3387-108">Ustawienia białej można zarówno utrwalić informacje, które są krytyczne dla aplikacji poza kod, aby utworzyć profile, których są przechowywane preferencje poszczególnych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="d3387-108">Settings allow you to both persist information that is critical to the application outside the code, and to create profiles that store the preferences of individual users.</span></span>  
  
 <span data-ttu-id="d3387-109">Tematy w tej sekcji opisano sposób używania ustawień w czasie projektowania i czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d3387-109">The topics in this section describe how to use settings at design time and run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d3387-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d3387-110">In This Section</span></span>  
 [<span data-ttu-id="d3387-111">Instrukcje: tworzenie nowego ustawienia w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="d3387-111">How To: Create a New Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md)  
  
 <span data-ttu-id="d3387-112">Wyjaśniono, jak utworzyć nowe ustawienie aplikacji za pomocą programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d3387-112">Explains how to use Visual Studio to create a new setting for an application.</span></span>  
  
 [<span data-ttu-id="d3387-113">Instrukcje: zmiana wartości istniejącego ustawienia w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="d3387-113">How To: Change the Value of an Existing Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)  
  
 <span data-ttu-id="d3387-114">W tym artykule opisano, jak zmiana wartości istniejącego ustawienia za pomocą programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d3387-114">Describes how to use Visual Studio to change the value of an existing setting.</span></span>  
  
 [<span data-ttu-id="d3387-115">Instrukcje: zmiana wartości ustawienia między sesjami aplikacji</span><span class="sxs-lookup"><span data-stu-id="d3387-115">How To: Change the Value of a Setting Between Application Sessions</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-a-setting-between-application-sessions.md)  
  
 <span data-ttu-id="d3387-116">Zawiera szczegóły dotyczące sposobu zmiany wartości ustawienia w skompilowanych aplikacji między sesjami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d3387-116">Details how to change the value of a setting in a compiled application between application sessions.</span></span>  
  
 [<span data-ttu-id="d3387-117">Instrukcje: czytanie ustawień w czasie wykonywania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d3387-117">How To: Read Settings at Run Time With C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="d3387-118">Opisuje sposób odczytać ustawień w języku C# za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="d3387-118">Describes how to use code to read settings with C#.</span></span>  
  
 [<span data-ttu-id="d3387-119">Instrukcje: pisanie ustawień użytkownika w czasie wykonywania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d3387-119">How To: Write User Settings at Run Time with C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="d3387-120">Wyjaśniono, jak użyć kodu, aby zapisać i zapisać wartości ustawień użytkownika w języku C#.</span><span class="sxs-lookup"><span data-stu-id="d3387-120">Explains how to use code to write and save the values of user settings with C#.</span></span>  
  
 [<span data-ttu-id="d3387-121">Instrukcje: dodawanie wielu zestawów ustawień do aplikacji w C#</span><span class="sxs-lookup"><span data-stu-id="d3387-121">How To: Add Multiple Sets of Settings To Your Application in C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-multiple-sets-of-settings-to-your-application-in-csharp.md)  
  
 <span data-ttu-id="d3387-122">Szczegółowe informacje dotyczące dodawania wielu zestawów ustawień do aplikacji w języku C#.</span><span class="sxs-lookup"><span data-stu-id="d3387-122">Details how to add multiple sets of settings to an application with C#.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3387-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3387-123">See Also</span></span>  
 [<span data-ttu-id="d3387-124">Ustawienia aplikacji dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3387-124">Application Settings for Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/application-settings-for-windows-forms.md)
