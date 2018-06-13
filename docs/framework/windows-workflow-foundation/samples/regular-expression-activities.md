---
title: Działania wyrażeń regularnych
ms.date: 03/30/2017
ms.assetid: b8f24694-49db-4339-92ec-014e3d4ae63b
ms.openlocfilehash: 34b1f18f26f0b79c4b8711d65da5707a85cf3bf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519837"
---
# <a name="regular-expression-activities"></a><span data-ttu-id="b70f9-102">Działania wyrażeń regularnych</span><span class="sxs-lookup"><span data-stu-id="b70f9-102">Regular Expression Activities</span></span>
<span data-ttu-id="b70f9-103">W tym przykładzie pokazano, jak utworzyć zestaw działań, które udostępniają funkcje wyrażenia regularnego <xref:System.Text.RegularExpressions> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b70f9-103">This sample demonstrates how to create a set of activities that expose the regular expression functionality of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="b70f9-104">Można używać tych działań niestandardowych aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b70f9-104">These custom activities can be used within a workflow application.</span></span> <span data-ttu-id="b70f9-105">Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz [N:System.Text.RegularExpressions](http://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span><span class="sxs-lookup"><span data-stu-id="b70f9-105">For more information about regular expressions, see [N:System.Text.RegularExpressions](http://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span></span>  
  
 <span data-ttu-id="b70f9-106">Poniższa tabela zawiera szczegóły dotyczące działania niestandardowe, w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b70f9-106">The following table details the custom activities in this sample.</span></span>  
  
|<span data-ttu-id="b70f9-107">Działanie</span><span class="sxs-lookup"><span data-stu-id="b70f9-107">Activity</span></span>|<span data-ttu-id="b70f9-108">Opis</span><span class="sxs-lookup"><span data-stu-id="b70f9-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="b70f9-109">IsMatch</span><span class="sxs-lookup"><span data-stu-id="b70f9-109">IsMatch</span></span>|<span data-ttu-id="b70f9-110">Określa, czy wyrażenie regularne Znaleziono dopasowanie w ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="b70f9-110">Specifies whether the regular expression found a match in the input string.</span></span>|  
|<span data-ttu-id="b70f9-111">Dopasowania</span><span class="sxs-lookup"><span data-stu-id="b70f9-111">Matches</span></span>|<span data-ttu-id="b70f9-112">Wyszukuje ciąg wejściowy dla wszystkich wystąpień elementu wyrażenia regularnego i zwraca wszystkie dopasowania powiodło się.</span><span class="sxs-lookup"><span data-stu-id="b70f9-112">Searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span>|  
|<span data-ttu-id="b70f9-113">Zamień</span><span class="sxs-lookup"><span data-stu-id="b70f9-113">Replace</span></span>|<span data-ttu-id="b70f9-114">W ramach określonego ciągu wejściowego zastępuje ciągi zgodne ze wzorcem wyrażenia regularnego z określony ciąg zastępczy.</span><span class="sxs-lookup"><span data-stu-id="b70f9-114">Within a specified input string, replaces strings that match a regular expression pattern with a specified replacement string.</span></span>|  
  
## <a name="ismatch"></a><span data-ttu-id="b70f9-115">IsMatch</span><span class="sxs-lookup"><span data-stu-id="b70f9-115">IsMatch</span></span>  
 <span data-ttu-id="b70f9-116">`IsMatch` Zwraca działania niestandardowego `true` Jeśli `Input` właściwości ciągu znalezieniu dopasowania z wyrażeniem regularnym określonym w `Pattern` właściwości.</span><span class="sxs-lookup"><span data-stu-id="b70f9-116">The `IsMatch` custom activity returns `true` if the `Input` string property finds a match in the regular expression specified in the `Pattern` property.</span></span> <span data-ttu-id="b70f9-117">Działanie jest pochodną <xref:System.Activities.CodeActivity%601> i poziomu <xref:System.Activities.CodeActivity%601.Execute%2A> wywołania metody <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b70f9-117">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method.</span></span>  
  
 <span data-ttu-id="b70f9-118">W poniższej tabeli opisano wartość właściwości i przywracać `IsMatch` działania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="b70f9-118">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="b70f9-119">Właściwości lub wartości zwracanej</span><span class="sxs-lookup"><span data-stu-id="b70f9-119">Property or Return Value</span></span>|<span data-ttu-id="b70f9-120">Opis</span><span class="sxs-lookup"><span data-stu-id="b70f9-120">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="b70f9-121">Wzorzec (wymagane)</span><span class="sxs-lookup"><span data-stu-id="b70f9-121">Pattern (required)</span></span>|<span data-ttu-id="b70f9-122">Wyrażenie regularne do wyszukania z.</span><span class="sxs-lookup"><span data-stu-id="b70f9-122">The regular expression to search with.</span></span>|  
|<span data-ttu-id="b70f9-123">Dane wejściowe (wymagane)</span><span class="sxs-lookup"><span data-stu-id="b70f9-123">Input (required)</span></span>|<span data-ttu-id="b70f9-124">Wejściowy ciąg do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="b70f9-124">The input string to search.</span></span>|  
|<span data-ttu-id="b70f9-125">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="b70f9-125">RegexOptions</span></span>|<span data-ttu-id="b70f9-126">Bitowe połączenie lub [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b70f9-126">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="b70f9-127">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b70f9-127">Return value</span></span>|<span data-ttu-id="b70f9-128">`true` Jeśli dane wejściowe znalezienia dopasowania we wzorcu podana; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="b70f9-128">`true` if the input finds a match in the provided pattern; otherwise `false`.</span></span>|  
  
 <span data-ttu-id="b70f9-129">Poniższy przykład kodu pokazuje sposób użycia `IsMatch` działania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="b70f9-129">The following code example demonstrates how to use the `IsMatch` custom activity.</span></span>  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a><span data-ttu-id="b70f9-130">Dopasowania</span><span class="sxs-lookup"><span data-stu-id="b70f9-130">Matches</span></span>  
 <span data-ttu-id="b70f9-131">`Matches` Działania niestandardowego wyszukuje ciąg wejściowy dla wszystkich wystąpień elementu wyrażenia regularnego i zwraca wszystkie dopasowania powiodło się.</span><span class="sxs-lookup"><span data-stu-id="b70f9-131">The `Matches` custom activity searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span> <span data-ttu-id="b70f9-132">Działanie jest pochodną <xref:System.Activities.CodeActivity%601> i poziomu <xref:System.Activities.CodeActivity%601.Execute%2A> wywołania metody <xref:System.Text.RegularExpressions.Regex.Matches%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b70f9-132">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Matches%2A> method.</span></span>  
  
 <span data-ttu-id="b70f9-133">W poniższej tabeli opisano wartość właściwości i przywracać `IsMatch` działania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="b70f9-133">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="b70f9-134">Właściwości lub wartości zwracanej</span><span class="sxs-lookup"><span data-stu-id="b70f9-134">Property or Return Value</span></span>|<span data-ttu-id="b70f9-135">Opis</span><span class="sxs-lookup"><span data-stu-id="b70f9-135">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="b70f9-136">Wzorzec (wymagane)</span><span class="sxs-lookup"><span data-stu-id="b70f9-136">Pattern (required)</span></span>|<span data-ttu-id="b70f9-137">Wyrażenie regularne do wyszukania z.</span><span class="sxs-lookup"><span data-stu-id="b70f9-137">The regular expression to search with.</span></span>|  
|<span data-ttu-id="b70f9-138">Dane wejściowe (wymagane)</span><span class="sxs-lookup"><span data-stu-id="b70f9-138">Input (required)</span></span>|<span data-ttu-id="b70f9-139">Wejściowy ciąg do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="b70f9-139">The input string to search.</span></span>|  
|<span data-ttu-id="b70f9-140">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="b70f9-140">RegexOptions</span></span>|<span data-ttu-id="b70f9-141">Bitowe połączenie lub [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b70f9-141">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="b70f9-142">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b70f9-142">Return Value</span></span>|<span data-ttu-id="b70f9-143">A <xref:System.Text.RegularExpressions.MatchCollection> zawierający kolekcja dopasowań powiodło się.</span><span class="sxs-lookup"><span data-stu-id="b70f9-143">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="b70f9-144">Poniższy przykład kodu pokazuje sposób użycia `Matches` działania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="b70f9-144">The following code example demonstrates how to use the `Matches` custom activity.</span></span>  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a><span data-ttu-id="b70f9-145">Zamień</span><span class="sxs-lookup"><span data-stu-id="b70f9-145">Replace</span></span>  
 <span data-ttu-id="b70f9-146">`Replace` Działania niestandardowego wyszukuje ciąg wejściowy i zastępuje wszystkie ciągi, które pasują do podanego wyrażenia regularnego z ciągiem.</span><span class="sxs-lookup"><span data-stu-id="b70f9-146">The `Replace` custom activity searches an input string and replaces all strings that match a specified regular expression with a string.</span></span> <span data-ttu-id="b70f9-147">Działanie jest pochodną <xref:System.Activities.CodeActivity%601> i poziomu <xref:System.Activities.CodeActivity%601.Execute%2A> wywołania metody <xref:System.Text.RegularExpressions.Regex.Replace%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b70f9-147">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Replace%2A> method.</span></span>  
  
 <span data-ttu-id="b70f9-148">W poniższej tabeli opisano wartość właściwości i przywracać `Replace` działania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="b70f9-148">The following table describes the properties and return value for the `Replace` custom activity.</span></span>  
  
|<span data-ttu-id="b70f9-149">Właściwości lub wartości zwracanej</span><span class="sxs-lookup"><span data-stu-id="b70f9-149">Property or Return Value</span></span>|<span data-ttu-id="b70f9-150">Opis</span><span class="sxs-lookup"><span data-stu-id="b70f9-150">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="b70f9-151">Wzorzec (wymagane)</span><span class="sxs-lookup"><span data-stu-id="b70f9-151">Pattern (required)</span></span>|<span data-ttu-id="b70f9-152">Wyrażenie regularne do wyszukania z.</span><span class="sxs-lookup"><span data-stu-id="b70f9-152">The regular expression to search with.</span></span>|  
|<span data-ttu-id="b70f9-153">Dane wejściowe (wymagane)</span><span class="sxs-lookup"><span data-stu-id="b70f9-153">Input (required)</span></span>|<span data-ttu-id="b70f9-154">Wejściowy ciąg do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="b70f9-154">The input string to search.</span></span>|  
|<span data-ttu-id="b70f9-155">Zastąpienie</span><span class="sxs-lookup"><span data-stu-id="b70f9-155">Replacement</span></span>|<span data-ttu-id="b70f9-156">Ciąg zastępujący.</span><span class="sxs-lookup"><span data-stu-id="b70f9-156">The replacement string.</span></span><br /><br /> <span data-ttu-id="b70f9-157">Jeśli `Replacement` jest określony, a następnie `MatchEvaluator` właściwość jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="b70f9-157">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="b70f9-158">Albo `Replacement` lub `MatchEvaluator` musi być ustawiona właściwość.</span><span class="sxs-lookup"><span data-stu-id="b70f9-158">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="b70f9-159">MatchEvaluator</span><span class="sxs-lookup"><span data-stu-id="b70f9-159">MatchEvaluator</span></span>|<span data-ttu-id="b70f9-160">Niestandardowe metody, która sprawdza każdym dopasowaniu i zwraca oryginalnego ciągu dopasowane lub ciąg zastępczy.</span><span class="sxs-lookup"><span data-stu-id="b70f9-160">A custom method that examines each match and returns either the original matched string or a replacement string.</span></span><br /><br /> <span data-ttu-id="b70f9-161">Jeśli `Replacement` jest określony, a następnie `MatchEvaluator` właściwość jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="b70f9-161">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="b70f9-162">Albo `Replacement` lub `MatchEvaluator` musi być ustawiona właściwość.</span><span class="sxs-lookup"><span data-stu-id="b70f9-162">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="b70f9-163">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="b70f9-163">RegexOptions</span></span>|<span data-ttu-id="b70f9-164">Bitowe połączenie lub [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b70f9-164">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="b70f9-165">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b70f9-165">Return Value</span></span>|<span data-ttu-id="b70f9-166">A <xref:System.Text.RegularExpressions.MatchCollection> zawierający kolekcja dopasowań powiodło się.</span><span class="sxs-lookup"><span data-stu-id="b70f9-166">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="b70f9-167">Poniższy przykład kodu pokazuje sposób użycia `Replace` działania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="b70f9-167">The following code example demonstrates how to use the `Replace` custom activity.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="b70f9-168">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="b70f9-168">To use this sample</span></span>  
  
1.  <span data-ttu-id="b70f9-169">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania RegexActivities.sln.</span><span class="sxs-lookup"><span data-stu-id="b70f9-169">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RegexActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="b70f9-170">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="b70f9-170">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="b70f9-171">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="b70f9-171">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b70f9-172">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b70f9-172">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b70f9-173">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b70f9-173">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b70f9-174">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="b70f9-174">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b70f9-175">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b70f9-175">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`