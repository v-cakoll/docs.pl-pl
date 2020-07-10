---
title: 'Porady: dodawanie wielu zestawów ustawień do aplikacji w C#'
description: Dowiedz się, jak dodać wiele zestawów ustawień Windows Forms do aplikacji w języku C# za pomocą programu Visual Studio.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 579374ff101758b3224bc122c46b891280ed2609
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173448"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="95bdf-103">Instrukcje: Dodawanie wielu zestawów ustawień do aplikacji w języku C\#</span><span class="sxs-lookup"><span data-stu-id="95bdf-103">How To: Add Multiple Sets of Settings To Your Application in C\#</span></span>

<span data-ttu-id="95bdf-104">W niektórych przypadkach może być konieczne posiadanie wielu zestawów ustawień w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="95bdf-104">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="95bdf-105">Na przykład w przypadku tworzenia aplikacji, w której oczekiwana jest zmiana konkretnej grupy ustawień, warto oddzielić je wszystkie w jednym pliku, aby można było wymienić ten plik, pozostawiając inne ustawienia bez zmian.</span><span class="sxs-lookup"><span data-stu-id="95bdf-105">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="95bdf-106">Program Visual Studio umożliwia dodanie wielu zestawów ustawień do projektu.</span><span class="sxs-lookup"><span data-stu-id="95bdf-106">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="95bdf-107">Dostęp do dodatkowych zestawów ustawień można uzyskać za pośrednictwem `Properties.Settings` obiektu.</span><span class="sxs-lookup"><span data-stu-id="95bdf-107">Additional sets of settings can be accessed via the `Properties.Settings` object.</span></span>

## <a name="add-an-additional-set-of-settings"></a><span data-ttu-id="95bdf-108">Dodaj dodatkowy zestaw ustawień</span><span class="sxs-lookup"><span data-stu-id="95bdf-108">Add an Additional Set of Settings</span></span>

1. <span data-ttu-id="95bdf-109">W programie Visual Studio w menu **projekt** wybierz polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="95bdf-109">In Visual Studio, from the **Project** menu, choose **Add New Item**.</span></span>

   <span data-ttu-id="95bdf-110">Zostanie otwarte okno dialogowe **Dodaj nowy element** .</span><span class="sxs-lookup"><span data-stu-id="95bdf-110">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="95bdf-111">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik ustawień**, wprowadź nazwę pliku, a następnie kliknij przycisk **Dodaj** , aby dodać nowy plik ustawień do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="95bdf-111">In the **Add New Item** dialog box, select **Settings File**, enter a name for the file, and click **Add** to add a new settings file to your solution.</span></span>

3. <span data-ttu-id="95bdf-112">W **Eksplorator rozwiązań**przeciągnij nowy plik ustawień do folderu **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="95bdf-112">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="95bdf-113">Dzięki temu nowe ustawienia będą dostępne w kodzie.</span><span class="sxs-lookup"><span data-stu-id="95bdf-113">This allows your new settings to be available in code.</span></span>

4. <span data-ttu-id="95bdf-114">Dodaj i Użyj ustawień w tym pliku, tak jak każdy inny plik ustawień.</span><span class="sxs-lookup"><span data-stu-id="95bdf-114">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="95bdf-115">Możesz uzyskać dostęp do tej grupy ustawień za pośrednictwem `Properties.Settings` obiektu.</span><span class="sxs-lookup"><span data-stu-id="95bdf-115">You can access this group of settings via the `Properties.Settings` object.</span></span>

## <a name="see-also"></a><span data-ttu-id="95bdf-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95bdf-116">See also</span></span>

- [<span data-ttu-id="95bdf-117">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="95bdf-117">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="95bdf-118">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="95bdf-118">Application Settings Overview</span></span>](application-settings-overview.md)
