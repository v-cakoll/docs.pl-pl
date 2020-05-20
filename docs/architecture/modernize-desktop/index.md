---
title: Modernizacja aplikacji klasycznych w systemie Windows 10 z platformą .NET Core 3,1
description: Dowiedz się, jak przeprowadzić modernizację istniejących aplikacji klasycznych za pomocą programu .NET Core 3,1
ms.date: 05/12/2020
ms.openlocfilehash: 5861f806a9158ef761c47bc23e51327d4e2d0480
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423237"
---
# <a name="modernizing-desktop-apps-on-windows-10-with-net-core-31"></a><span data-ttu-id="9cfa2-103">Modernizacja aplikacji klasycznych w systemie Windows 10 z platformą .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="9cfa2-103">Modernizing Desktop Apps on Windows 10 with .NET Core 3.1</span></span>

![Zrzut ekranu pokazujący modernizację książki elektronicznej aplikacji klasycznych.](./media/modernizing-existing-desktop-apps-ebook-cover.png)

<span data-ttu-id="9cfa2-105">OPUBLIKOWANA PRZEZ</span><span class="sxs-lookup"><span data-stu-id="9cfa2-105">PUBLISHED BY</span></span>

<span data-ttu-id="9cfa2-106">Zespoły deweloperów firmy Microsoft, .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9cfa2-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="9cfa2-107">Dział firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="9cfa2-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="9cfa2-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="9cfa2-108">One Microsoft Way</span></span>

<span data-ttu-id="9cfa2-109">Redmond, Waszyngton 98052-6399</span><span class="sxs-lookup"><span data-stu-id="9cfa2-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="9cfa2-110">Prawa autorskie © 2020 przez firmę Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="9cfa2-110">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="9cfa2-111">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-111">All rights reserved.</span></span> <span data-ttu-id="9cfa2-112">Żadna część zawartości tej księgi nie może być odtwarzana ani przekazywana w żadnej formie ani za pomocą jakichkolwiek środków bez zgody na wydawcę.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="9cfa2-113">Ta książka jest świadczona w postaci "AS-IS" i zawiera widoki i opinie autora.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="9cfa2-114">Widoki, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odwołania do witryn internetowych, mogą ulec zmianie bez powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="9cfa2-115">Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="9cfa2-116">Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="9cfa2-117">Firma Microsoft i znaki towarowe wymienione na <https://www.microsoft.com> stronie "znaki towarowe" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-117">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="9cfa2-118">Komputery Mac i macOS są znakami towarowymi firmy Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="9cfa2-119">Wszystkie inne znaczniki i logo są własnością odpowiednich właścicieli.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="9cfa2-120">Współautorzy:</span><span class="sxs-lookup"><span data-stu-id="9cfa2-120">Co-Authors:</span></span>

> <span data-ttu-id="9cfa2-121">**Olia Gavrysh**, Menedżer programów, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9cfa2-121">**Olia Gavrysh**, Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="9cfa2-122">**Miguel Angel Castejón Dominguez**, architekt innowacji, kabel</span><span class="sxs-lookup"><span data-stu-id="9cfa2-122">**Miguel Angel Castejón Dominguez**, Innovation Architect, Kabel</span></span>

<span data-ttu-id="9cfa2-123">Uczestnicy i recenzenci:</span><span class="sxs-lookup"><span data-stu-id="9cfa2-123">Participants and reviewers:</span></span>

> <span data-ttu-id="9cfa2-124">**Maira Wenzel**, starszy kierownik ds. programów, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9cfa2-124">**Maira Wenzel**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="9cfa2-125">**Adam de Gorge**, starszy dla deweloperów zawartości, zespół ds. dokumentacji platformy .NET, firma Microsoft</span><span class="sxs-lookup"><span data-stu-id="9cfa2-125">**Andy De Gorge**, Senior Content Developer, .NET docs team, Microsoft</span></span>

> <span data-ttu-id="9cfa2-126">**Miguel Ramos**, starszy kierownik ds. programu, zespół platformy dla deweloperów systemu Windows, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9cfa2-126">**Miguel Ramos**, Senior Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="9cfa2-127">**Adam Braden**, główny Menedżer programu, zespół platformy deweloperów systemu Windows, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9cfa2-127">**Adam Braden**, Principal Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="9cfa2-128">**Ricardo Minguez Pablos**, starszy Menedżer programów, Azure IoT Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9cfa2-128">**Ricardo Minguez Pablos**, Senior Program Manager, Azure IoT team, Microsoft</span></span>

> <span data-ttu-id="9cfa2-129">**Nish Anil**, starszy kierownik ds. programów, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9cfa2-129">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="9cfa2-130">**Beth Massi**, starszy kierownik ds. marketingu produktu, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9cfa2-130">**Beth Massi**, Senior Product Marketing Manager, Microsoft</span></span>

> <span data-ttu-id="9cfa2-131">**Scott myśliwy**, kierownik ds. programów dyrektora</span><span class="sxs-lookup"><span data-stu-id="9cfa2-131">**Scott Hunter**, Partner Director Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="9cfa2-132">**Marta Fuentes Lara**, kabel</span><span class="sxs-lookup"><span data-stu-id="9cfa2-132">**Marta Fuentes Lara**, Kabel</span></span>

> <span data-ttu-id="9cfa2-133">**Raúl Fernández de Córdoba**, kabel</span><span class="sxs-lookup"><span data-stu-id="9cfa2-133">**Raúl Fernández de Córdoba**, Kabel</span></span>

> <span data-ttu-id="9cfa2-134">**Antonio Manuel Fernández Cantos**, kabel</span><span class="sxs-lookup"><span data-stu-id="9cfa2-134">**Antonio Manuel Fernández Cantos**, Kabel</span></span>

## <a name="introduction"></a><span data-ttu-id="9cfa2-135">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="9cfa2-135">Introduction</span></span>

<span data-ttu-id="9cfa2-136">Ta książka zawiera informacje o strategiach, które można podjąć w celu przeniesienia istniejących aplikacji klasycznych za pomocą ścieżki modernizacji i uwzględnienia najnowszych funkcji środowiska uruchomieniowego, języka i platformy.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-136">This book is about strategies you can adopt to move your existing desktop applications through the path of modernization and incorporate the latest runtime, language, and platform features.</span></span> <span data-ttu-id="9cfa2-137">Zobaczysz, że nie ma żadnych unikatowych przepisów, ponieważ każda aplikacja jest inna, a więc wymagania i preferencje.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-137">You'll discover that there's no unique recipe as each application is different, and so are your requirements and preferences.</span></span> <span data-ttu-id="9cfa2-138">Dobrym sposobem jest to, że istnieją typowe podejścia do dodawania nowych funkcji i możliwości do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-138">The good news is that there are common approaches you can apply to add new features and capabilities to your applications.</span></span> <span data-ttu-id="9cfa2-139">Niektóre z nich nie będą nawet wymagały poważnych modyfikacji kodu.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-139">Some of them won't even require major modifications of your code.</span></span> <span data-ttu-id="9cfa2-140">W tej książce będziemy odkrywać, jak wszystkie funkcje działają w tle, i wyjaśnić Mechanics ich implementacji.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-140">In this book, we'll reveal how all those features work behind the scenes and explain the mechanics of their implementations.</span></span> <span data-ttu-id="9cfa2-141">Ponadto znajdziesz typowe scenariusze dotyczące modernizacji istniejących aplikacji klasycznych, aby znaleźć inspirację do rozwoju projektów.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-141">Moreover, you'll find some common scenarios for modernizing existing desktop applications shown in detail so you can find inspiration for evolving your projects.</span></span>

<span data-ttu-id="9cfa2-142">Podejście firmy Microsoft do modernizacji istniejących aplikacji ma na celu elastyczność tworzenia własnej dostosowanej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-142">Microsoft's approach to modernizing existing applications is to give you the flexibility to create your own customized path.</span></span> <span data-ttu-id="9cfa2-143">Wszystkie strategie modernizacji opisane w tej książce są głównie niezależne.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-143">All the modernization strategies described in this book are mostly independent.</span></span> <span data-ttu-id="9cfa2-144">Możesz wybrać odpowiednie dla aplikacji i pominąć inne, które nie są dla Ciebie ważne.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-144">You can choose ones that are relevant for your application and skip others that aren't important for you.</span></span> <span data-ttu-id="9cfa2-145">Innymi słowy, można mieszać i dopasowywać strategie, aby najlepiej rozwiązać wymagania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-145">In other words, you can mix and match the strategies to best address your application needs.</span></span>

## <a name="who-should-use-the-book"></a><span data-ttu-id="9cfa2-146">Kto powinien korzystać z książki</span><span class="sxs-lookup"><span data-stu-id="9cfa2-146">Who should use the book</span></span>

<span data-ttu-id="9cfa2-147">Ta książka została zapisana dla deweloperów i architektów rozwiązań, którzy chcą przeprowadzić modernizację istniejących Windows Forms i aplikacji klasycznych WPF, aby wykorzystać zalety platformy .NET Core i systemu Windows 10.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-147">We wrote this book for developers and solution architects who want to modernize existing Windows Forms and WPF desktop applications to leverage the benefits of .NET Core and Windows 10.</span></span>

<span data-ttu-id="9cfa2-148">Ta książka może być również przydatna, jeśli jesteś specjalistą ds. pomocy technicznej, na przykład z architektem przedsiębiorstwa lub liderem programistycznym lub dyrektorem, który chce zapoznać się z zaletami aktualizacji istniejących aplikacji klasycznych.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-148">You might also find this book useful if you're a technical decision maker, such as an enterprise architect or a development lead or director who wants an overview of the benefits of updating existing desktop applications.</span></span>

## <a name="how-to-use-the-book"></a><span data-ttu-id="9cfa2-149">Jak korzystać z książki</span><span class="sxs-lookup"><span data-stu-id="9cfa2-149">How to use the book</span></span>

<span data-ttu-id="9cfa2-150">Ta książka dotyczy "Dlaczego" — Dlaczego warto przeprowadzić modernizację istniejących aplikacji oraz konkretne korzyści wynikające z używania NET Core 3,1 i MSIX do modernizacji aplikacji klasycznych.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-150">This book addresses the "why"—why you might want to modernize your existing applications, and the specific benefits you get from using NET Core 3.1 and MSIX to modernize your desktop apps.</span></span> <span data-ttu-id="9cfa2-151">Zawartość książki jest przeznaczona dla architektów i osób podejmujących decyzje techniczne, którzy chcą zapoznać się z omówieniem, ale którzy nie muszą skupić się na implementacji i technicznych krokach krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-151">The content of the book is designed for architects and technical decision makers who want an overview, but who don't need to focus on implementation and technical, step-by-step details.</span></span>

<span data-ttu-id="9cfa2-152">Wraz z różnymi rozdziałami są udostępniane przykładowe fragmenty kodu implementacji i zrzuty ekranu z rozdziałem 5 w celu zaprezentowania kompletnego procesu migracji dla przykładowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-152">Along the different chapters, sample implementation code snippets and screenshots are provided, with chapter 5 devoted to showcase a complete migration process for sample applications.</span></span>

## <a name="what-this-book-doesnt-cover"></a><span data-ttu-id="9cfa2-153">Czym nie obejmuje ta książka</span><span class="sxs-lookup"><span data-stu-id="9cfa2-153">What this book doesn't cover</span></span>

<span data-ttu-id="9cfa2-154">Ta książka obejmuje określony podzbiór scenariuszy, które koncentrują się na scenariuszach podnoszenia i przesunięcia, i podkreślają sposób uzyskania korzyści z modernizacji bez wysiłku ponownego pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-154">This book covers a specific subset of scenarios that are focused on lift-and-shift scenarios, outlining the way to gain the benefits of modernizing without the effort of rewriting code.</span></span>

<span data-ttu-id="9cfa2-155">Ta książka nie dotyczy tworzenia nowoczesnych aplikacji z użyciem platformy .NET Core od podstaw lub od rozpoczęcia korzystania z Windows Forms i WPF.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-155">This book isn't about developing modern applications with .NET Core from scratch or about getting started with Windows Forms and WPF.</span></span> <span data-ttu-id="9cfa2-156">Koncentruje się na sposobach aktualizowania istniejących aplikacji klasycznych przy użyciu najnowszych technologii tworzenia oprogramowania dla komputerów stacjonarnych.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-156">It focuses on how you can update existing desktop applications with the latest technologies for desktop development.</span></span>

## <a name="samples-used-in-this-book"></a><span data-ttu-id="9cfa2-157">Przykłady używane w tej książce</span><span class="sxs-lookup"><span data-stu-id="9cfa2-157">Samples used in this book</span></span>

<span data-ttu-id="9cfa2-158">Aby wyróżnić kroki niezbędne do wykonania modernizacji, użyjemy przykładowej aplikacji o nazwie `eShopModernizing` .</span><span class="sxs-lookup"><span data-stu-id="9cfa2-158">To highlight the necessary steps to perform a modernization, we'll be using a sample application called `eShopModernizing`.</span></span> <span data-ttu-id="9cfa2-159">Ta aplikacja ma dwa wersje, Windows Forms i WPF, a następnie pokazuje proces krok po kroku dotyczący sposobu przeprowadzania modernizacji na obu tych platformach w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-159">This application has two flavors, Windows Forms and WPF, and we'll show a step-by-step process on how to perform the modernization on both of them to .NET Core.</span></span>

<span data-ttu-id="9cfa2-160">Ponadto w repozytorium GitHub dla tej książki znajdziesz wyniki procesu, z którym możesz się zapoznać, jeśli zdecydujesz się wykonać instrukcje krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="9cfa2-160">Also, on the GitHub repository for this book, you'll find the results of the process, which you can consult with if you decide to follow the step-by-step tutorial.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="9cfa2-161">Wyślij opinię</span><span class="sxs-lookup"><span data-stu-id="9cfa2-161">Send your feedback</span></span>

<span data-ttu-id="9cfa2-162">Ta książka i powiązane przykłady są ciągle zmieniane, dzięki czemu Twoje opinie są gotowe!</span><span class="sxs-lookup"><span data-stu-id="9cfa2-162">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="9cfa2-163">Jeśli masz komentarze dotyczące sposobu, w jaki można ulepszyć tę książkę, Skorzystaj z sekcji opinia w dolnej części strony utworzonej w witrynie [GitHub](https://github.com/dotnet/docs/issues).</span><span class="sxs-lookup"><span data-stu-id="9cfa2-163">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="9cfa2-164">Dalej</span><span class="sxs-lookup"><span data-stu-id="9cfa2-164">Next</span></span>](why-modern-applications.md)
