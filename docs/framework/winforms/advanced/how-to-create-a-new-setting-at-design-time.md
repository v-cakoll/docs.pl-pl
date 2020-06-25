---
title: 'Porady: tworzenie nowego ustawienia w czasie projektowania'
description: Dowiedz się, jak utworzyć nowe ustawienie Windows Forms w czasie projektowania przy użyciu projektanta ustawień w programie Visual Studio.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: ce37b42191999e29de2f2f7f7e7abfa0ec3f4d47
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325842"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="08237-103">Instrukcje: Tworzenie nowego ustawienia w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="08237-103">How To: Create a new setting at design time</span></span>

<span data-ttu-id="08237-104">Nowe ustawienie można utworzyć w czasie projektowania przy użyciu projektanta ustawień w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="08237-104">You can create a new setting at design time by using the Settings designer in Visual Studio.</span></span> <span data-ttu-id="08237-105">Projektant ustawień jest interfejsem stylu siatki, który umożliwia tworzenie nowych ustawień i określanie właściwości tych ustawień.</span><span class="sxs-lookup"><span data-stu-id="08237-105">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="08237-106">Należy określić nazwę, wartość, typ i zakres dla nowych ustawień.</span><span class="sxs-lookup"><span data-stu-id="08237-106">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="08237-107">Po utworzeniu ustawienia jest ono dostępne w kodzie.</span><span class="sxs-lookup"><span data-stu-id="08237-107">Once a setting is created, it is accessible in code.</span></span>

## <a name="create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="08237-108">Tworzenie nowego ustawienia w czasie projektowania w języku C\#</span><span class="sxs-lookup"><span data-stu-id="08237-108">Create a new setting at design time in C\#</span></span>

1. <span data-ttu-id="08237-109">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="08237-109">Open Visual Studio.</span></span>

2. <span data-ttu-id="08237-110">W **Eksplorator rozwiązań**rozwiń węzeł **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="08237-110">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>

3. <span data-ttu-id="08237-111">Kliknij dwukrotnie plik ustawień, w którym chcesz dodać nowe ustawienie.</span><span class="sxs-lookup"><span data-stu-id="08237-111">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="08237-112">Domyślna nazwa tego pliku to Settings. Settings.</span><span class="sxs-lookup"><span data-stu-id="08237-112">The default name for this file is Settings.settings.</span></span>

4. <span data-ttu-id="08237-113">W projektancie ustawień Ustaw **nazwę**, **wartość**, **Typ**i **zakres** dla ustawienia.</span><span class="sxs-lookup"><span data-stu-id="08237-113">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="08237-114">Każdy wiersz reprezentuje jedno ustawienie.</span><span class="sxs-lookup"><span data-stu-id="08237-114">Each row represents a single setting.</span></span>

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="08237-115">Utwórz nowe ustawienie w czasie projektowania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="08237-115">Create a new setting at design time in Visual Basic</span></span>

1. <span data-ttu-id="08237-116">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="08237-116">Open Visual Studio.</span></span>

2. <span data-ttu-id="08237-117">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="08237-117">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>

3. <span data-ttu-id="08237-118">Na stronie **Właściwości** wybierz kartę **Ustawienia** .</span><span class="sxs-lookup"><span data-stu-id="08237-118">In the **Properties** page, select the **Settings** tab.</span></span>

4. <span data-ttu-id="08237-119">W projektancie ustawień Ustaw **nazwę**, **wartość**, **Typ**i **zakres** dla ustawienia.</span><span class="sxs-lookup"><span data-stu-id="08237-119">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="08237-120">Każdy wiersz reprezentuje jedno ustawienie.</span><span class="sxs-lookup"><span data-stu-id="08237-120">Each row represents a single setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="08237-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08237-121">See also</span></span>

- [<span data-ttu-id="08237-122">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="08237-122">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="08237-123">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="08237-123">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="08237-124">Porady: zmiana wartości istniejącego ustawienia w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="08237-124">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
