---
title: Używanie ustawień aplikacji i ustawień użytkownika
ms.date: 03/30/2017
description: Dowiedz się, jak używać ustawień aplikacji i ustawień użytkownika do tworzenia i uzyskiwania dostępu do wartości utrwalanych między sesjami wykonywania aplikacji.
helpviewer_keywords:
- user settings [Windows Forms]
- application settings [Windows Forms], how-to topics
ms.assetid: 54682d3b-1cbf-4683-9351-012b8b4286b5
ms.openlocfilehash: a30fd354986265eca002fce57bccf5b3bb2adc15
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903171"
---
# <a name="using-application-settings-and-user-settings"></a><span data-ttu-id="e12c6-103">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="e12c6-103">Using Application Settings and User Settings</span></span>
<span data-ttu-id="e12c6-104">Począwszy od .NET Framework 2,0, można tworzyć i uzyskiwać dostęp do wartości utrwalanych między sesjami wykonywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e12c6-104">Starting with the .NET Framework 2.0, you can create and access values that are persisted between application execution sessions.</span></span> <span data-ttu-id="e12c6-105">Te wartości są nazywane *ustawieniami*.</span><span class="sxs-lookup"><span data-stu-id="e12c6-105">These values are called *settings*.</span></span> <span data-ttu-id="e12c6-106">Ustawienia mogą reprezentować preferencje użytkownika lub cenne informacje wymagane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="e12c6-106">Settings can represent user preferences, or valuable information the application needs to use.</span></span> <span data-ttu-id="e12c6-107">Można na przykład utworzyć serię ustawień, które przechowują preferencje użytkownika dla schematu kolorów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e12c6-107">For example, you might create a series of settings that store user preferences for the color scheme of an application.</span></span> <span data-ttu-id="e12c6-108">Lub można przechowywać parametry połączenia określające bazę danych używaną przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="e12c6-108">Or you might store the connection string that specifies a database that your application uses.</span></span> <span data-ttu-id="e12c6-109">Ustawienia umożliwiają zarówno utrwalać informacje, które są krytyczne dla aplikacji poza kodem, jak i utworzyć profile, które przechowują preferencje poszczególnych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="e12c6-109">Settings allow you to both persist information that is critical to the application outside the code, and to create profiles that store the preferences of individual users.</span></span>  
  
 <span data-ttu-id="e12c6-110">W tematach w tej sekcji opisano, jak używać ustawień w czasie projektowania i w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e12c6-110">The topics in this section describe how to use settings at design time and run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e12c6-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e12c6-111">In This Section</span></span>  
 [<span data-ttu-id="e12c6-112">Instrukcje: tworzenie nowego ustawienia w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="e12c6-112">How To: Create a New Setting at Design Time</span></span>](how-to-create-a-new-setting-at-design-time.md)  
  
 <span data-ttu-id="e12c6-113">Wyjaśnia, jak użyć programu Visual Studio do utworzenia nowego ustawienia dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e12c6-113">Explains how to use Visual Studio to create a new setting for an application.</span></span>  
  
 [<span data-ttu-id="e12c6-114">Porady: zmiana wartości istniejącego ustawienia w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="e12c6-114">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)  
  
 <span data-ttu-id="e12c6-115">Opisuje sposób użycia programu Visual Studio do zmiany wartości istniejącego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="e12c6-115">Describes how to use Visual Studio to change the value of an existing setting.</span></span>  
  
 [<span data-ttu-id="e12c6-116">Instrukcje: zmiana wartości ustawienia między sesjami aplikacji</span><span class="sxs-lookup"><span data-stu-id="e12c6-116">How To: Change the Value of a Setting Between Application Sessions</span></span>](how-to-change-the-value-of-a-setting-between-application-sessions.md)  
  
 <span data-ttu-id="e12c6-117">Szczegóły dotyczące zmiany wartości ustawienia w skompilowanej aplikacji między sesjami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e12c6-117">Details how to change the value of a setting in a compiled application between application sessions.</span></span>  
  
 [<span data-ttu-id="e12c6-118">Porady: czytanie ustawień w czasie wykonywania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e12c6-118">How To: Read Settings at Run Time With C#</span></span>](how-to-read-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="e12c6-119">Opisuje sposób używania kodu do odczytywania ustawień przy użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="e12c6-119">Describes how to use code to read settings with C#.</span></span>  
  
 [<span data-ttu-id="e12c6-120">Instrukcje: pisanie ustawień użytkownika w czasie wykonywania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e12c6-120">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="e12c6-121">Wyjaśnia, w jaki sposób używać kodu do zapisywania i zapisywania wartości ustawień użytkownika w języku C#.</span><span class="sxs-lookup"><span data-stu-id="e12c6-121">Explains how to use code to write and save the values of user settings with C#.</span></span>  
  
 [<span data-ttu-id="e12c6-122">Instrukcje: dodawanie wielu zestawów ustawień do aplikacji w C#</span><span class="sxs-lookup"><span data-stu-id="e12c6-122">How To: Add Multiple Sets of Settings To Your Application in C#</span></span>](how-to-add-multiple-sets-of-settings-to-your-application-in-csharp.md)  
  
 <span data-ttu-id="e12c6-123">Szczegóły dotyczące dodawania wielu zestawów ustawień do aplikacji przy użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="e12c6-123">Details how to add multiple sets of settings to an application with C#.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e12c6-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e12c6-124">See also</span></span>

- [<span data-ttu-id="e12c6-125">Ustawienia aplikacji dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e12c6-125">Application Settings for Windows Forms</span></span>](application-settings-for-windows-forms.md)
