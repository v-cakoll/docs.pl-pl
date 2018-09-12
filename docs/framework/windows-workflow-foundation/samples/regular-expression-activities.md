---
title: Regularne wyrażenia działań
ms.date: 03/30/2017
ms.assetid: b8f24694-49db-4339-92ec-014e3d4ae63b
ms.openlocfilehash: 50daa5b6d7baab37f372de4c30c2e0d12b4fa943
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44509885"
---
# <a name="regular-expression-activities"></a><span data-ttu-id="75045-102">Regularne wyrażenia działań</span><span class="sxs-lookup"><span data-stu-id="75045-102">Regular Expression Activities</span></span>
<span data-ttu-id="75045-103">W tym przykładzie pokazano, jak utworzyć zestaw działań, które udostępniają funkcje wyrażenia regularnego <xref:System.Text.RegularExpressions> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="75045-103">This sample demonstrates how to create a set of activities that expose the regular expression functionality of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="75045-104">Te niestandardowe działania może służyć w aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="75045-104">These custom activities can be used within a workflow application.</span></span> <span data-ttu-id="75045-105">Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz [N:System.Text.RegularExpressions](https://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span><span class="sxs-lookup"><span data-stu-id="75045-105">For more information about regular expressions, see [N:System.Text.RegularExpressions](https://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span></span>  
  
 <span data-ttu-id="75045-106">W poniższej tabeli przedstawiono niestandardowych działań w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="75045-106">The following table details the custom activities in this sample.</span></span>  
  
|<span data-ttu-id="75045-107">Działanie</span><span class="sxs-lookup"><span data-stu-id="75045-107">Activity</span></span>|<span data-ttu-id="75045-108">Opis</span><span class="sxs-lookup"><span data-stu-id="75045-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="75045-109">IsMatch</span><span class="sxs-lookup"><span data-stu-id="75045-109">IsMatch</span></span>|<span data-ttu-id="75045-110">Określa, czy wyrażenie regularne Znaleziono dopasowanie w ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="75045-110">Specifies whether the regular expression found a match in the input string.</span></span>|  
|<span data-ttu-id="75045-111">Dopasowania</span><span class="sxs-lookup"><span data-stu-id="75045-111">Matches</span></span>|<span data-ttu-id="75045-112">Wyszukuje ciąg wejściowy dla wszystkich wystąpień elementu wyrażenia regularnego i zwraca wszystkie pomyślnego dopasowania.</span><span class="sxs-lookup"><span data-stu-id="75045-112">Searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span>|  
|<span data-ttu-id="75045-113">Zastąp</span><span class="sxs-lookup"><span data-stu-id="75045-113">Replace</span></span>|<span data-ttu-id="75045-114">W ramach określonego ciągu wejściowego zastępuje ciągów, które pasują do wzorca wyrażenia regularnego przy użyciu określony ciąg zastępczy.</span><span class="sxs-lookup"><span data-stu-id="75045-114">Within a specified input string, replaces strings that match a regular expression pattern with a specified replacement string.</span></span>|  
  
## <a name="ismatch"></a><span data-ttu-id="75045-115">IsMatch</span><span class="sxs-lookup"><span data-stu-id="75045-115">IsMatch</span></span>  
 <span data-ttu-id="75045-116">`IsMatch` Zwraca niestandardowe działanie `true` Jeśli `Input` właściwość ciągu umożliwia znalezienie zgodny z wyrażeniem regularnym określonym w `Pattern` właściwości.</span><span class="sxs-lookup"><span data-stu-id="75045-116">The `IsMatch` custom activity returns `true` if the `Input` string property finds a match in the regular expression specified in the `Pattern` property.</span></span> <span data-ttu-id="75045-117">Działanie jest pochodną <xref:System.Activities.CodeActivity%601> i poziomu <xref:System.Activities.CodeActivity%601.Execute%2A> wywołania metody <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="75045-117">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method.</span></span>  
  
 <span data-ttu-id="75045-118">W poniższej tabeli opisano właściwości i wartość zwracana dla `IsMatch` działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="75045-118">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="75045-119">Właściwości lub wartości zwracanej</span><span class="sxs-lookup"><span data-stu-id="75045-119">Property or Return Value</span></span>|<span data-ttu-id="75045-120">Opis</span><span class="sxs-lookup"><span data-stu-id="75045-120">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="75045-121">Wzorzec (wymagane)</span><span class="sxs-lookup"><span data-stu-id="75045-121">Pattern (required)</span></span>|<span data-ttu-id="75045-122">Wyrażenie regularne do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="75045-122">The regular expression to search with.</span></span>|  
|<span data-ttu-id="75045-123">Dane wejściowe (wymagane)</span><span class="sxs-lookup"><span data-stu-id="75045-123">Input (required)</span></span>|<span data-ttu-id="75045-124">Wejściowy ciąg do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="75045-124">The input string to search.</span></span>|  
|<span data-ttu-id="75045-125">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="75045-125">RegexOptions</span></span>|<span data-ttu-id="75045-126">Bitową kombinacją OR [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="75045-126">Bitwise OR combination of [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="75045-127">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="75045-127">Return value</span></span>|<span data-ttu-id="75045-128">`true` Jeśli dane wejściowe znajdzie dopasowanie we wzorcu podana; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="75045-128">`true` if the input finds a match in the provided pattern; otherwise `false`.</span></span>|  
  
 <span data-ttu-id="75045-129">Poniższy przykład kodu demonstruje sposób używania `IsMatch` działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="75045-129">The following code example demonstrates how to use the `IsMatch` custom activity.</span></span>  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a><span data-ttu-id="75045-130">Dopasowania</span><span class="sxs-lookup"><span data-stu-id="75045-130">Matches</span></span>  
 <span data-ttu-id="75045-131">`Matches` Niestandardowe działanie wyszukuje ciąg wejściowy dla wszystkich wystąpień elementu wyrażenia regularnego i zwraca wszystkie pomyślnego dopasowania.</span><span class="sxs-lookup"><span data-stu-id="75045-131">The `Matches` custom activity searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span> <span data-ttu-id="75045-132">Działanie jest pochodną <xref:System.Activities.CodeActivity%601> i poziomu <xref:System.Activities.CodeActivity%601.Execute%2A> wywołania metody <xref:System.Text.RegularExpressions.Regex.Matches%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="75045-132">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Matches%2A> method.</span></span>  
  
 <span data-ttu-id="75045-133">W poniższej tabeli opisano właściwości i wartość zwracana dla `IsMatch` działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="75045-133">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="75045-134">Właściwości lub wartości zwracanej</span><span class="sxs-lookup"><span data-stu-id="75045-134">Property or Return Value</span></span>|<span data-ttu-id="75045-135">Opis</span><span class="sxs-lookup"><span data-stu-id="75045-135">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="75045-136">Wzorzec (wymagane)</span><span class="sxs-lookup"><span data-stu-id="75045-136">Pattern (required)</span></span>|<span data-ttu-id="75045-137">Wyrażenie regularne do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="75045-137">The regular expression to search with.</span></span>|  
|<span data-ttu-id="75045-138">Dane wejściowe (wymagane)</span><span class="sxs-lookup"><span data-stu-id="75045-138">Input (required)</span></span>|<span data-ttu-id="75045-139">Wejściowy ciąg do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="75045-139">The input string to search.</span></span>|  
|<span data-ttu-id="75045-140">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="75045-140">RegexOptions</span></span>|<span data-ttu-id="75045-141">Bitową kombinacją OR [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="75045-141">Bitwise OR combination of [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="75045-142">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="75045-142">Return Value</span></span>|<span data-ttu-id="75045-143">A <xref:System.Text.RegularExpressions.MatchCollection> , która zawiera kolekcję dopasowań.</span><span class="sxs-lookup"><span data-stu-id="75045-143">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="75045-144">Poniższy przykład kodu demonstruje sposób używania `Matches` działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="75045-144">The following code example demonstrates how to use the `Matches` custom activity.</span></span>  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a><span data-ttu-id="75045-145">Zastąp</span><span class="sxs-lookup"><span data-stu-id="75045-145">Replace</span></span>  
 <span data-ttu-id="75045-146">`Replace` Niestandardowe działanie wyszukuje ciąg wejściowy i zastępuje wszystkie ciągi, które pasują do określonego wyrażenia regularnego z ciągiem.</span><span class="sxs-lookup"><span data-stu-id="75045-146">The `Replace` custom activity searches an input string and replaces all strings that match a specified regular expression with a string.</span></span> <span data-ttu-id="75045-147">Działanie jest pochodną <xref:System.Activities.CodeActivity%601> i poziomu <xref:System.Activities.CodeActivity%601.Execute%2A> wywołania metody <xref:System.Text.RegularExpressions.Regex.Replace%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="75045-147">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Replace%2A> method.</span></span>  
  
 <span data-ttu-id="75045-148">W poniższej tabeli opisano właściwości i wartość zwracana dla `Replace` działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="75045-148">The following table describes the properties and return value for the `Replace` custom activity.</span></span>  
  
|<span data-ttu-id="75045-149">Właściwości lub wartości zwracanej</span><span class="sxs-lookup"><span data-stu-id="75045-149">Property or Return Value</span></span>|<span data-ttu-id="75045-150">Opis</span><span class="sxs-lookup"><span data-stu-id="75045-150">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="75045-151">Wzorzec (wymagane)</span><span class="sxs-lookup"><span data-stu-id="75045-151">Pattern (required)</span></span>|<span data-ttu-id="75045-152">Wyrażenie regularne do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="75045-152">The regular expression to search with.</span></span>|  
|<span data-ttu-id="75045-153">Dane wejściowe (wymagane)</span><span class="sxs-lookup"><span data-stu-id="75045-153">Input (required)</span></span>|<span data-ttu-id="75045-154">Wejściowy ciąg do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="75045-154">The input string to search.</span></span>|  
|<span data-ttu-id="75045-155">Zastępczy</span><span class="sxs-lookup"><span data-stu-id="75045-155">Replacement</span></span>|<span data-ttu-id="75045-156">Ciąg zastępujący.</span><span class="sxs-lookup"><span data-stu-id="75045-156">The replacement string.</span></span><br /><br /> <span data-ttu-id="75045-157">Jeśli `Replacement` jest określony, a następnie `MatchEvaluator` właściwość jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="75045-157">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="75045-158">Albo `Replacement` lub `MatchEvaluator` musi być ustawiona właściwość.</span><span class="sxs-lookup"><span data-stu-id="75045-158">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="75045-159">MatchEvaluator</span><span class="sxs-lookup"><span data-stu-id="75045-159">MatchEvaluator</span></span>|<span data-ttu-id="75045-160">Niestandardowe metody, która sprawdza każdego dopasowania i zwraca oryginalny ciąg dopasowane lub ciąg zastępujący.</span><span class="sxs-lookup"><span data-stu-id="75045-160">A custom method that examines each match and returns either the original matched string or a replacement string.</span></span><br /><br /> <span data-ttu-id="75045-161">Jeśli `Replacement` jest określony, a następnie `MatchEvaluator` właściwość jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="75045-161">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="75045-162">Albo `Replacement` lub `MatchEvaluator` musi być ustawiona właściwość.</span><span class="sxs-lookup"><span data-stu-id="75045-162">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="75045-163">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="75045-163">RegexOptions</span></span>|<span data-ttu-id="75045-164">Bitową kombinacją OR [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="75045-164">Bitwise OR combination of [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="75045-165">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="75045-165">Return Value</span></span>|<span data-ttu-id="75045-166">A <xref:System.Text.RegularExpressions.MatchCollection> , która zawiera kolekcję dopasowań.</span><span class="sxs-lookup"><span data-stu-id="75045-166">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="75045-167">Poniższy przykład kodu demonstruje sposób używania `Replace` działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="75045-167">The following code example demonstrates how to use the `Replace` custom activity.</span></span>  
  
```  
// Using the replacement string.  
new Replace  
{  
    Pattern = @"\bWorld\b",  
    Input = "Hello World! This is a wonderful World",  
    Replacement = "Universe"  
};  
  
// Using a match evaluator.  
new Replace  
{  
    Pattern = new InArgument<string>(pattern),  
    Input = new InArgument<string>(input),  
    MatchEvaluator = new MatchEvaluator(CapText)                  
};  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="75045-168">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="75045-168">To use this sample</span></span>  
  
1.  <span data-ttu-id="75045-169">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania RegexActivities.sln.</span><span class="sxs-lookup"><span data-stu-id="75045-169">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RegexActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="75045-170">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="75045-170">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="75045-171">Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="75045-171">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="75045-172">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="75045-172">The samples may already be installed on your machine.</span></span> <span data-ttu-id="75045-173">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="75045-173">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="75045-174">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="75045-174">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="75045-175">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="75045-175">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`