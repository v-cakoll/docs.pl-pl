---
title: Używanie działań proceduralnych
ms.date: 03/30/2017
ms.assetid: 1c67f739-3878-48ad-806c-b2ce0d6733a0
ms.openlocfilehash: bd83f1a0fa9f3af7c22cee73fbc4f984a9ebf53c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732043"
---
# <a name="using-procedural-activities"></a><span data-ttu-id="2d65d-102">Używanie działań proceduralnych</span><span class="sxs-lookup"><span data-stu-id="2d65d-102">Using Procedural Activities</span></span>
<span data-ttu-id="2d65d-103">W przykładzie użyto <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, i <xref:System.Activities.Statements.WriteLine> działania, aby zaimplementować zgadywania gier.</span><span class="sxs-lookup"><span data-stu-id="2d65d-103">The sample uses the <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, and <xref:System.Activities.Statements.WriteLine> activities to implement a guessing game.</span></span> <span data-ttu-id="2d65d-104">Odgadnięcia gier wybiera losową liczbę, a gracz musi odgadnięcia tę liczbę.</span><span class="sxs-lookup"><span data-stu-id="2d65d-104">The guessing game selects a random number and the player has to guess that number.</span></span> <span data-ttu-id="2d65d-105">Gdy gracz wyśle nieprawidłowy wynik, przepływ pracy stanowi wskazówkę czy odgadnięcia wyższy lub niższy.</span><span class="sxs-lookup"><span data-stu-id="2d65d-105">When the player submits an incorrect guess, the workflow provides a hint whether to guess higher or lower.</span></span> <span data-ttu-id="2d65d-106">Jeśli gracz próby odgadnięcia numer w przypadku prób ataków mniej niż 7, Gratulujemy specjalne jest wyświetlany użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="2d65d-106">If the player guesses the number in less than 7 attempts, a special congratulations is displayed to the user.</span></span>  
  
## <a name="custom-activities-in-this-sample"></a><span data-ttu-id="2d65d-107">Niestandardowe działania w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="2d65d-107">Custom Activities in this Sample</span></span>  
  
### <a name="readline"></a><span data-ttu-id="2d65d-108">ReadLine</span><span class="sxs-lookup"><span data-stu-id="2d65d-108">ReadLine</span></span>  
 <span data-ttu-id="2d65d-109">Odczytuje wiersz tekstu z konsoli.</span><span class="sxs-lookup"><span data-stu-id="2d65d-109">Reads a line of text from the console.</span></span> <span data-ttu-id="2d65d-110">To działanie jest pochodną <xref:System.Activities.NativeActivity> klasy i tworzy zakładki, która zostanie wznowione przez aplikację konsoli, jeśli wiersz jest do odczytu.</span><span class="sxs-lookup"><span data-stu-id="2d65d-110">This activity derives from the <xref:System.Activities.NativeActivity> class and creates a bookmark that is resumed by the console application when a line is read.</span></span>  
  
### <a name="promptint"></a><span data-ttu-id="2d65d-111">PromptInt</span><span class="sxs-lookup"><span data-stu-id="2d65d-111">PromptInt</span></span>  
 <span data-ttu-id="2d65d-112">Monituje użytkownika o wpisanie liczby w, a następnie odczytuje z okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="2d65d-112">Prompts the user to type in a number and then reads it from a console window.</span></span> <span data-ttu-id="2d65d-113">Działanie jest pochodną <xref:System.Activities.Activity%601> i używa <xref:System.Activities.Statements.WriteLine> i `ReadLine` działań.</span><span class="sxs-lookup"><span data-stu-id="2d65d-113">The activity derives from <xref:System.Activities.Activity%601> and uses the <xref:System.Activities.Statements.WriteLine> and `ReadLine` activities.</span></span>  
  
##### <a name="to-use-this-sample"></a><span data-ttu-id="2d65d-114">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="2d65d-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="2d65d-115">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania GuessingGame.sln.</span><span class="sxs-lookup"><span data-stu-id="2d65d-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the GuessingGame.sln solution file.</span></span>  
  
2.  <span data-ttu-id="2d65d-116">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="2d65d-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="2d65d-117">Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="2d65d-117">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2d65d-118">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2d65d-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2d65d-119">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2d65d-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2d65d-120">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="2d65d-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2d65d-121">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d65d-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Procedurals`