---
title: Używanie ustawień aplikacji i ustawień użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- user settings [Windows Forms]
- application settings [Windows Forms], how-to topics
ms.assetid: 54682d3b-1cbf-4683-9351-012b8b4286b5
ms.openlocfilehash: ea6994e653b3a06239634f5a0fddea84a07086e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777185"
---
# <a name="using-application-settings-and-user-settings"></a><span data-ttu-id="146ae-102">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="146ae-102">Using Application Settings and User Settings</span></span>
<span data-ttu-id="146ae-103">Począwszy od programu .NET Framework 2.0, można tworzyć i uzyskać dostęp do wartości, które są zachowywane między sesjami wykonywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="146ae-103">Starting with the .NET Framework 2.0, you can create and access values that are persisted between application execution sessions.</span></span> <span data-ttu-id="146ae-104">Wartości te są nazywane *ustawienia*.</span><span class="sxs-lookup"><span data-stu-id="146ae-104">These values are called *settings*.</span></span> <span data-ttu-id="146ae-105">Ustawienia mogą być reprezentowane preferencji użytkownika lub cenne informacje aplikacji musi używać.</span><span class="sxs-lookup"><span data-stu-id="146ae-105">Settings can represent user preferences, or valuable information the application needs to use.</span></span> <span data-ttu-id="146ae-106">Na przykład może utworzyć szereg ustawień, których są przechowywane preferencje użytkownika dotyczące schemat kolorów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="146ae-106">For example, you might create a series of settings that store user preferences for the color scheme of an application.</span></span> <span data-ttu-id="146ae-107">Lub można przechowywać parametry połączenia, które określa bazę danych, używanych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="146ae-107">Or you might store the connection string that specifies a database that your application uses.</span></span> <span data-ttu-id="146ae-108">Ustawienia Zezwalaj na monit zarówno utrwalić informacje, które mają kluczowe znaczenie dla aplikacji poza kodem i tworzyć profile, które przechowują Preferencje poszczególnych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="146ae-108">Settings allow you to both persist information that is critical to the application outside the code, and to create profiles that store the preferences of individual users.</span></span>  
  
 <span data-ttu-id="146ae-109">Tematy w tej sekcji opisano sposób użycia ustawienia w czasie projektowania i w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="146ae-109">The topics in this section describe how to use settings at design time and run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="146ae-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="146ae-110">In This Section</span></span>  
 [<span data-ttu-id="146ae-111">Instrukcje: Utwórz nowe ustawienie w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="146ae-111">How To: Create a New Setting at Design Time</span></span>](how-to-create-a-new-setting-at-design-time.md)  
  
 <span data-ttu-id="146ae-112">Wyjaśnia, jak utworzyć nowe ustawienie aplikacji przy użyciu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="146ae-112">Explains how to use Visual Studio to create a new setting for an application.</span></span>  
  
 [<span data-ttu-id="146ae-113">Instrukcje: Zmiana wartości istniejącego ustawienia w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="146ae-113">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)  
  
 <span data-ttu-id="146ae-114">W tym artykule opisano, jak zmiana wartości istniejącego ustawienia za pomocą programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="146ae-114">Describes how to use Visual Studio to change the value of an existing setting.</span></span>  
  
 [<span data-ttu-id="146ae-115">Instrukcje: Zmiana wartości ustawienia między sesjami aplikacji</span><span class="sxs-lookup"><span data-stu-id="146ae-115">How To: Change the Value of a Setting Between Application Sessions</span></span>](how-to-change-the-value-of-a-setting-between-application-sessions.md)  
  
 <span data-ttu-id="146ae-116">Szczegółowe informacje, jak zmienić wartość ustawienia w skompilowanej aplikacji między sesjami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="146ae-116">Details how to change the value of a setting in a compiled application between application sessions.</span></span>  
  
 [<span data-ttu-id="146ae-117">Instrukcje: Odczytaj ustawienia w czasie wykonywania za pomocąC#</span><span class="sxs-lookup"><span data-stu-id="146ae-117">How To: Read Settings at Run Time With C#</span></span>](how-to-read-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="146ae-118">Opisuje sposób używania kodu do odczytu ustawień za pomocą C#.</span><span class="sxs-lookup"><span data-stu-id="146ae-118">Describes how to use code to read settings with C#.</span></span>  
  
 [<span data-ttu-id="146ae-119">Instrukcje: Pisanie ustawień użytkownika w czasie wykonywania w językuC#</span><span class="sxs-lookup"><span data-stu-id="146ae-119">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="146ae-120">Wyjaśnia, jak używać kodu do zapisywania i zapisać wartości ustawień użytkownika z C#.</span><span class="sxs-lookup"><span data-stu-id="146ae-120">Explains how to use code to write and save the values of user settings with C#.</span></span>  
  
 [<span data-ttu-id="146ae-121">Instrukcje: Dodawanie wielu zestawów ustawień do aplikacji wC#</span><span class="sxs-lookup"><span data-stu-id="146ae-121">How To: Add Multiple Sets of Settings To Your Application in C#</span></span>](how-to-add-multiple-sets-of-settings-to-your-application-in-csharp.md)  
  
 <span data-ttu-id="146ae-122">Szczegóły sposobu dodawania wielu zestawów ustawień do aplikacji za pomocą C#.</span><span class="sxs-lookup"><span data-stu-id="146ae-122">Details how to add multiple sets of settings to an application with C#.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="146ae-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="146ae-123">See also</span></span>

- [<span data-ttu-id="146ae-124">Ustawienia aplikacji dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="146ae-124">Application Settings for Windows Forms</span></span>](application-settings-for-windows-forms.md)
