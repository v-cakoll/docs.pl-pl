---
title: 'Instrukcje: Dodawanie wielu zestawów ustawień do aplikacji w C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: c6842d11c04e905d42734af939f2c3f0cfeacd47
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040123"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="d9aad-102">Instrukcje: Dodawanie wielu zestawów ustawień do aplikacji w języku C\#</span><span class="sxs-lookup"><span data-stu-id="d9aad-102">How To: Add Multiple Sets of Settings To Your Application in C\#</span></span>

<span data-ttu-id="d9aad-103">W niektórych przypadkach może być konieczne posiadanie wielu zestawów ustawień w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d9aad-103">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="d9aad-104">Na przykład w przypadku tworzenia aplikacji, w której oczekiwana jest zmiana konkretnej grupy ustawień, warto oddzielić je wszystkie w jednym pliku, aby można było wymienić ten plik, pozostawiając inne ustawienia bez zmian.</span><span class="sxs-lookup"><span data-stu-id="d9aad-104">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="d9aad-105">Program Visual Studio umożliwia dodanie wielu zestawów ustawień do projektu.</span><span class="sxs-lookup"><span data-stu-id="d9aad-105">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="d9aad-106">Dostęp do dodatkowych zestawów ustawień można uzyskać za pośrednictwem `Properties.Settings` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d9aad-106">Additional sets of settings can be accessed via the `Properties.Settings` object.</span></span>

## <a name="add-an-additional-set-of-settings"></a><span data-ttu-id="d9aad-107">Dodaj dodatkowy zestaw ustawień</span><span class="sxs-lookup"><span data-stu-id="d9aad-107">Add an Additional Set of Settings</span></span>

1. <span data-ttu-id="d9aad-108">W programie Visual Studio w menu **projekt** wybierz polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="d9aad-108">In Visual Studio, from the **Project** menu, choose **Add New Item**.</span></span>

   <span data-ttu-id="d9aad-109">**Dodaj nowy element** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d9aad-109">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="d9aad-110">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik ustawień**, wprowadź nazwę pliku, a następnie kliknij przycisk **Dodaj** , aby dodać nowy plik ustawień do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d9aad-110">In the **Add New Item** dialog box, select **Settings File**, enter a name for the file, and click **Add** to add a new settings file to your solution.</span></span>

3. <span data-ttu-id="d9aad-111">W **Eksplorator rozwiązań**przeciągnij nowy plik ustawień do folderu **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="d9aad-111">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="d9aad-112">Dzięki temu nowe ustawienia będą dostępne w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d9aad-112">This allows your new settings to be available in code.</span></span>

4. <span data-ttu-id="d9aad-113">Dodaj i Użyj ustawień w tym pliku, tak jak każdy inny plik ustawień.</span><span class="sxs-lookup"><span data-stu-id="d9aad-113">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="d9aad-114">Możesz uzyskać dostęp do tej grupy ustawień za pośrednictwem `Properties.Settings` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d9aad-114">You can access this group of settings via the `Properties.Settings` object.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9aad-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9aad-115">See also</span></span>

- [<span data-ttu-id="d9aad-116">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="d9aad-116">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="d9aad-117">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="d9aad-117">Application Settings Overview</span></span>](application-settings-overview.md)
