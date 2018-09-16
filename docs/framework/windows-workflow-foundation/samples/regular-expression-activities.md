---
title: Regularne wyrażenia działań
ms.date: 03/30/2017
ms.assetid: b8f24694-49db-4339-92ec-014e3d4ae63b
ms.openlocfilehash: 50daa5b6d7baab37f372de4c30c2e0d12b4fa943
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45668954"
---
# <a name="regular-expression-activities"></a>Regularne wyrażenia działań
W tym przykładzie pokazano, jak utworzyć zestaw działań, które udostępniają funkcje wyrażenia regularnego <xref:System.Text.RegularExpressions> przestrzeni nazw. Te niestandardowe działania może służyć w aplikacji przepływu pracy. Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz [N:System.Text.RegularExpressions](https://go.microsoft.com/fwlink/?LinkId=150434) Namespace.  
  
 W poniższej tabeli przedstawiono niestandardowych działań w tym przykładzie.  
  
|Działanie|Opis|  
|--------------|-----------------|  
|IsMatch|Określa, czy wyrażenie regularne Znaleziono dopasowanie w ciągu wejściowym.|  
|Dopasowania|Wyszukuje ciąg wejściowy dla wszystkich wystąpień elementu wyrażenia regularnego i zwraca wszystkie pomyślnego dopasowania.|  
|Zastąp|W ramach określonego ciągu wejściowego zastępuje ciągów, które pasują do wzorca wyrażenia regularnego przy użyciu określony ciąg zastępczy.|  
  
## <a name="ismatch"></a>IsMatch  
 `IsMatch` Zwraca niestandardowe działanie `true` Jeśli `Input` właściwość ciągu umożliwia znalezienie zgodny z wyrażeniem regularnym określonym w `Pattern` właściwości. Działanie jest pochodną <xref:System.Activities.CodeActivity%601> i poziomu <xref:System.Activities.CodeActivity%601.Execute%2A> wywołania metody <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metody.  
  
 W poniższej tabeli opisano właściwości i wartość zwracana dla `IsMatch` działań niestandardowych.  
  
|Właściwości lub wartości zwracanej|Opis|  
|------------------------------|-----------------|  
|Wzorzec (wymagane)|Wyrażenie regularne do wyszukiwania.|  
|Dane wejściowe (wymagane)|Wejściowy ciąg do wyszukania.|  
|RegexOptions|Bitową kombinacją OR [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) wartości wyliczenia.|  
|Wartość zwracana|`true` Jeśli dane wejściowe znajdzie dopasowanie we wzorcu podana; w przeciwnym razie `false`.|  
  
 Poniższy przykład kodu demonstruje sposób używania `IsMatch` działań niestandardowych.  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a>Dopasowania  
 `Matches` Niestandardowe działanie wyszukuje ciąg wejściowy dla wszystkich wystąpień elementu wyrażenia regularnego i zwraca wszystkie pomyślnego dopasowania. Działanie jest pochodną <xref:System.Activities.CodeActivity%601> i poziomu <xref:System.Activities.CodeActivity%601.Execute%2A> wywołania metody <xref:System.Text.RegularExpressions.Regex.Matches%2A> metody.  
  
 W poniższej tabeli opisano właściwości i wartość zwracana dla `IsMatch` działań niestandardowych.  
  
|Właściwości lub wartości zwracanej|Opis|  
|------------------------------|-----------------|  
|Wzorzec (wymagane)|Wyrażenie regularne do wyszukiwania.|  
|Dane wejściowe (wymagane)|Wejściowy ciąg do wyszukania.|  
|RegexOptions|Bitową kombinacją OR [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) wartości wyliczenia.|  
|Wartość zwracana|A <xref:System.Text.RegularExpressions.MatchCollection> , która zawiera kolekcję dopasowań.|  
  
 Poniższy przykład kodu demonstruje sposób używania `Matches` działań niestandardowych.  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a>Zastąp  
 `Replace` Niestandardowe działanie wyszukuje ciąg wejściowy i zastępuje wszystkie ciągi, które pasują do określonego wyrażenia regularnego z ciągiem. Działanie jest pochodną <xref:System.Activities.CodeActivity%601> i poziomu <xref:System.Activities.CodeActivity%601.Execute%2A> wywołania metody <xref:System.Text.RegularExpressions.Regex.Replace%2A> metody.  
  
 W poniższej tabeli opisano właściwości i wartość zwracana dla `Replace` działań niestandardowych.  
  
|Właściwości lub wartości zwracanej|Opis|  
|------------------------------|-----------------|  
|Wzorzec (wymagane)|Wyrażenie regularne do wyszukiwania.|  
|Dane wejściowe (wymagane)|Wejściowy ciąg do wyszukania.|  
|Zastępczy|Ciąg zastępujący.<br /><br /> Jeśli `Replacement` jest określony, a następnie `MatchEvaluator` właściwość jest ignorowana. Albo `Replacement` lub `MatchEvaluator` musi być ustawiona właściwość.|  
|MatchEvaluator|Niestandardowe metody, która sprawdza każdego dopasowania i zwraca oryginalny ciąg dopasowane lub ciąg zastępujący.<br /><br /> Jeśli `Replacement` jest określony, a następnie `MatchEvaluator` właściwość jest ignorowana. Albo `Replacement` lub `MatchEvaluator` musi być ustawiona właściwość.|  
|RegexOptions|Bitową kombinacją OR [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) wartości wyliczenia.|  
|Wartość zwracana|A <xref:System.Text.RegularExpressions.MatchCollection> , która zawiera kolekcję dopasowań.|  
  
 Poniższy przykład kodu demonstruje sposób używania `Replace` działań niestandardowych.  
  
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
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania RegexActivities.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`