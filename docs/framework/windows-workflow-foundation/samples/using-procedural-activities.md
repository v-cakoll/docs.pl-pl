---
title: "Przy użyciu procedur działań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c67f739-3878-48ad-806c-b2ce0d6733a0
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 05b4dc09ee1301366c95b447d767219460c46f99
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="using-procedural-activities"></a><span data-ttu-id="91e2b-102">Przy użyciu procedur działań</span><span class="sxs-lookup"><span data-stu-id="91e2b-102">Using Procedural Activities</span></span>
<span data-ttu-id="91e2b-103">W przykładzie użyto <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, i <xref:System.Activities.Statements.WriteLine> działań do wykonania odgadnięcie gier.</span><span class="sxs-lookup"><span data-stu-id="91e2b-103">The sample uses the <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, and <xref:System.Activities.Statements.WriteLine> activities to implement a guessing game.</span></span> <span data-ttu-id="91e2b-104">Gry guessing wybiera liczbę losową i odtwarzacz ma odgadnąć ten numer.</span><span class="sxs-lookup"><span data-stu-id="91e2b-104">The guessing game selects a random number and the player has to guess that number.</span></span> <span data-ttu-id="91e2b-105">Gdy odtwarzacz wyśle nieprawidłowy wynik, przepływ pracy podpowiada czy odgadnąć wyższy lub niższy.</span><span class="sxs-lookup"><span data-stu-id="91e2b-105">When the player submits an incorrect guess, the workflow provides a hint whether to guess higher or lower.</span></span> <span data-ttu-id="91e2b-106">Jeśli odtwarzacz liczba prób numer w mniej niż 7 prób, Gratulujemy specjalne jest wyświetlana użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="91e2b-106">If the player guesses the number in less than 7 attempts, a special congratulations is displayed to the user.</span></span>  
  
## <a name="custom-activities-in-this-sample"></a><span data-ttu-id="91e2b-107">Niestandardowe działania w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="91e2b-107">Custom Activities in this Sample</span></span>  
  
### <a name="readline"></a><span data-ttu-id="91e2b-108">ReadLine</span><span class="sxs-lookup"><span data-stu-id="91e2b-108">ReadLine</span></span>  
 <span data-ttu-id="91e2b-109">Odczytuje wiersz tekstu z konsoli.</span><span class="sxs-lookup"><span data-stu-id="91e2b-109">Reads a line of text from the console.</span></span> <span data-ttu-id="91e2b-110">To działanie jest pochodną <xref:System.Activities.NativeActivity> klasy i tworzy zakładki, która zostanie wznowione przez aplikację konsoli, jeśli wiersz jest do odczytu.</span><span class="sxs-lookup"><span data-stu-id="91e2b-110">This activity derives from the <xref:System.Activities.NativeActivity> class and creates a bookmark that is resumed by the console application when a line is read.</span></span>  
  
### <a name="promptint"></a><span data-ttu-id="91e2b-111">PromptInt</span><span class="sxs-lookup"><span data-stu-id="91e2b-111">PromptInt</span></span>  
 <span data-ttu-id="91e2b-112">Monituje użytkownika o wpisz numer i odczytuje go z okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="91e2b-112">Prompts the user to type in a number and then reads it from a console window.</span></span> <span data-ttu-id="91e2b-113">Działanie jest pochodną <xref:System.Activities.Activity%601> i używa <xref:System.Activities.Statements.WriteLine> i `ReadLine` działań.</span><span class="sxs-lookup"><span data-stu-id="91e2b-113">The activity derives from <xref:System.Activities.Activity%601> and uses the <xref:System.Activities.Statements.WriteLine> and `ReadLine` activities.</span></span>  
  
##### <a name="to-use-this-sample"></a><span data-ttu-id="91e2b-114">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="91e2b-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="91e2b-115">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania GuessingGame.sln.</span><span class="sxs-lookup"><span data-stu-id="91e2b-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the GuessingGame.sln solution file.</span></span>  
  
2.  <span data-ttu-id="91e2b-116">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="91e2b-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="91e2b-117">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="91e2b-117">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="91e2b-118">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="91e2b-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="91e2b-119">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="91e2b-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="91e2b-120">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="91e2b-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="91e2b-121">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="91e2b-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Procedurals`