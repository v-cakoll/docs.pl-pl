---
title: 'Instrukcje: Tworzenie nowego ustawienia w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: 35a7cd8cc1daaf76a25977751ddc9ec0709e5947
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037905"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="a2b6d-102">Instrukcje: Tworzenie nowego ustawienia w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="a2b6d-102">How To: Create a new setting at design time</span></span>

<span data-ttu-id="a2b6d-103">Nowe ustawienie można utworzyć w czasie projektowania przy użyciu projektanta ustawień w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a2b6d-103">You can create a new setting at design time by using the Settings designer in Visual Studio.</span></span> <span data-ttu-id="a2b6d-104">Projektant ustawień jest interfejsem stylu siatki, który umożliwia tworzenie nowych ustawień i określanie właściwości tych ustawień.</span><span class="sxs-lookup"><span data-stu-id="a2b6d-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="a2b6d-105">Należy określić nazwę, wartość, typ i zakres dla nowych ustawień.</span><span class="sxs-lookup"><span data-stu-id="a2b6d-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="a2b6d-106">Po utworzeniu ustawienia jest ono dostępne w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a2b6d-106">Once a setting is created, it is accessible in code.</span></span>

## <a name="create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="a2b6d-107">Tworzenie nowego ustawienia w czasie projektowania w języku C\#</span><span class="sxs-lookup"><span data-stu-id="a2b6d-107">Create a new setting at design time in C\#</span></span>

1. <span data-ttu-id="a2b6d-108">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a2b6d-108">Open Visual Studio.</span></span>

2. <span data-ttu-id="a2b6d-109">W **Eksplorator rozwiązań**rozwiń węzeł **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="a2b6d-109">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>

3. <span data-ttu-id="a2b6d-110">Kliknij dwukrotnie plik ustawień, w którym chcesz dodać nowe ustawienie.</span><span class="sxs-lookup"><span data-stu-id="a2b6d-110">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="a2b6d-111">Domyślna nazwa tego pliku to Settings. Settings.</span><span class="sxs-lookup"><span data-stu-id="a2b6d-111">The default name for this file is Settings.settings.</span></span>

4. <span data-ttu-id="a2b6d-112">W projektancie ustawień Ustaw **nazwę**, **wartość**, **Typ**i **zakres** dla ustawienia.</span><span class="sxs-lookup"><span data-stu-id="a2b6d-112">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="a2b6d-113">Każdy wiersz reprezentuje jedno ustawienie.</span><span class="sxs-lookup"><span data-stu-id="a2b6d-113">Each row represents a single setting.</span></span>

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="a2b6d-114">Utwórz nowe ustawienie w czasie projektowania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a2b6d-114">Create a new setting at design time in Visual Basic</span></span>

1. <span data-ttu-id="a2b6d-115">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a2b6d-115">Open Visual Studio.</span></span>

2. <span data-ttu-id="a2b6d-116">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="a2b6d-116">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>

3. <span data-ttu-id="a2b6d-117">Na stronie **Właściwości** wybierz kartę **Ustawienia** .</span><span class="sxs-lookup"><span data-stu-id="a2b6d-117">In the **Properties** page, select the **Settings** tab.</span></span>

4. <span data-ttu-id="a2b6d-118">W projektancie ustawień Ustaw **nazwę**, **wartość**, **Typ**i **zakres** dla ustawienia.</span><span class="sxs-lookup"><span data-stu-id="a2b6d-118">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="a2b6d-119">Każdy wiersz reprezentuje jedno ustawienie.</span><span class="sxs-lookup"><span data-stu-id="a2b6d-119">Each row represents a single setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2b6d-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2b6d-120">See also</span></span>

- [<span data-ttu-id="a2b6d-121">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="a2b6d-121">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="a2b6d-122">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="a2b6d-122">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="a2b6d-123">Instrukcje: Zmiana wartości istniejącego ustawienia w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="a2b6d-123">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
