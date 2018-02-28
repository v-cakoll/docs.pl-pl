---
title: "Roslyn analizatorów — na podstawie .NET"
description: "Więcej informacji na temat analizatorów Roslyn na podstawie, znaleźć problemy, które sugeruje rozwiązania tych problemów."
keywords: .NET, .NET Core
author: billwagner
ms.author: billwagner
ms.date: 01/24/2018
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.openlocfilehash: 8c6524716ba403bc426df8dc33e64b8b2934d3d7
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2018
---
# <a name="the-roslyn-based-analyzers"></a><span data-ttu-id="4bb20-104">Analizatory na podstawie Roslyn</span><span class="sxs-lookup"><span data-stu-id="4bb20-104">The Roslyn based Analyzers</span></span>

<span data-ttu-id="4bb20-105">Na podstawie Roslyn analizatorów umożliwia analizowanie kodu źródłowego projektu, aby znaleźć problemy i zaproponuje poprawki zestawu .NET SDK kompilatora (Roslyn API).</span><span class="sxs-lookup"><span data-stu-id="4bb20-105">Roslyn-based analyzers use the .NET Compiler SDK (Roslyn APIs) to analyze your project's source code to find issues and suggest corrections.</span></span> <span data-ttu-id="4bb20-106">Różne analizatorów poszukaj różne rodzaje problemów, począwszy od rozwiązania, które mogą spowodować usterki do zagadnienia dotyczące zabezpieczeń w celu zgodności z interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="4bb20-106">Different analyzers look for different classes of issues, ranging from practices that are likely to cause bugs to security concerns to API compatibility.</span></span>

<span data-ttu-id="4bb20-107">Na podstawie Roslyn analizatorów działa zarówno interakcyjne i podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4bb20-107">Roslyn-based analyzers work both interactively and during builds.</span></span> <span data-ttu-id="4bb20-108">Analizatora znajdują się różne wskazówki w Visual Studio lub w kompilacji z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4bb20-108">The analyzer provides different guidance when in Visual Studio or in command-line builds.</span></span>

<span data-ttu-id="4bb20-109">Podczas edytowania kodu w programie Visual Studio analizatorów Uruchom jako wprowadzić zmiany, przechwytywanie możliwych problemach, jak tworzyć kod wyzwolenia problemy.</span><span class="sxs-lookup"><span data-stu-id="4bb20-109">While you edit code in Visual Studio, the analyzers run as you make changes, catching possible issues as soon as you create code that trigger concerns.</span></span> <span data-ttu-id="4bb20-110">Wszystkie problemy zostały wyróżnione z zygzaki w jakikolwiek problem.</span><span class="sxs-lookup"><span data-stu-id="4bb20-110">Any issues are highlighted with squiggles under any issue.</span></span> <span data-ttu-id="4bb20-111">Żarówka Wyświetla programu Visual Studio, a po jego kliknięciu analizatora sugeruje możliwe rozwiązania tego problemu.</span><span class="sxs-lookup"><span data-stu-id="4bb20-111">Visual Studio displays a light bulb, and when you click on it the analyzer will suggest possible fixes for that issue.</span></span> <span data-ttu-id="4bb20-112">Podczas kompilowania projektu programu Visual Studio lub z wiersza polecenia analizy kodu źródłowego i analizatora zawiera pełną listę potencjalnych problemów.</span><span class="sxs-lookup"><span data-stu-id="4bb20-112">When you build the project, either in Visual Studio or from the command line, all the source code is analyzed and the analyzer provides a full list of potential issues.</span></span> <span data-ttu-id="4bb20-113">Na poniższej ilustracji przedstawiono przykład.</span><span class="sxs-lookup"><span data-stu-id="4bb20-113">The following figure shows one example.</span></span>

![problemy zgłoszone przez analizator framework](./media/framework-analyzers-2.png)

<span data-ttu-id="4bb20-115">Na podstawie Roslyn analizatorów raport potencjalnych problemach, jak błędy, ostrzeżenia lub informacji na podstawie ich wagi problemu.</span><span class="sxs-lookup"><span data-stu-id="4bb20-115">Roslyn-based analyzers report potential issues as errors, warnings, or information based on the severity of the issue.</span></span>

<span data-ttu-id="4bb20-116">Na podstawie Roslyn analizatorów jest instalowany jako pakietów NuGet w projekcie.</span><span class="sxs-lookup"><span data-stu-id="4bb20-116">You install Roslyn-based analyzers as NuGet packages in your project.</span></span> <span data-ttu-id="4bb20-117">Skonfigurowany analizatorów wszystkie ustawienia dla każdego analizatora przywrócona i uruchomić na maszynie Każdy deweloper dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="4bb20-117">The configured analyzers and any settings for each analyzer are restored and run on any developer's machine for that project.</span></span>

> [!NOTE]
> <span data-ttu-id="4bb20-118">Środowisko użytkownika na podstawie Roslyn analizatorów jest inny niż z biblioteki analizy kodu, takich jak starszych wersji programu FxCop oraz narzędzia do analizy zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="4bb20-118">The user experience for Roslyn-based analyzers is different than that of the Code Analysis libraries like the older versions of FxCop and the security analysis tools.</span></span>  <span data-ttu-id="4bb20-119">Nie trzeba uruchomić na podstawie Roslyn analizatorów.</span><span class="sxs-lookup"><span data-stu-id="4bb20-119">You don't need to explicitly run the Roslyn-based analyzers.</span></span> <span data-ttu-id="4bb20-120">Nie istnieje potrzeba użycie elementów menu "Uruchom analizę kodu" w menu "Analyze" w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4bb20-120">There's no need to use the "Run Code Analysis" menu items on the "Analyze" menu in Visual Studio.</span></span> <span data-ttu-id="4bb20-121">Na podstawie Roslyn analizatorów Uruchom asychronously podczas pracy.</span><span class="sxs-lookup"><span data-stu-id="4bb20-121">Roslyn-based analyzers run asychronously as you work.</span></span> 

## <a name="more-information-on-specific-analyzers"></a><span data-ttu-id="4bb20-122">Więcej informacji na temat określonych analizatorów</span><span class="sxs-lookup"><span data-stu-id="4bb20-122">More information on specific analyzers</span></span>

<span data-ttu-id="4bb20-123">Następujące analizatorów zostały omówione w tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="4bb20-123">The following analyzers are covered in this section:</span></span>

<span data-ttu-id="4bb20-124">[Analizator interfejsu API](api-analyzer.md): ten analyzer sprawdza, czy kod dla potencjalnych zagrożeń zgodności lub korzysta z interfejsów API przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="4bb20-124">[API Analyzer](api-analyzer.md): This analyzer examines your code for potential compatibility risks or uses of deprecated APIs.</span></span>    
<span data-ttu-id="4bb20-125">[Analizator Framework](framework-analyzer.md): ten analyzer sprawdza swój kod, aby upewnić się, wynika z wytycznymi dla aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4bb20-125">[Framework Analyzer](framework-analyzer.md): This analyzer examines your code to ensure it follows the guidelines for .NET Framework applications.</span></span> <span data-ttu-id="4bb20-126">Reguły obejmują kilka zabezpieczeń na podstawie zalecenia.</span><span class="sxs-lookup"><span data-stu-id="4bb20-126">These rules include several security-based recommendations.</span></span>
