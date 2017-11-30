---
title: "Działania wyrażeń regularnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8f24694-49db-4339-92ec-014e3d4ae63b
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c04b5c97feb7843a5120e3b2171e132526caa961
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="regular-expression-activities"></a>Działania wyrażeń regularnych
W tym przykładzie pokazano, jak utworzyć zestaw działań, które udostępniają funkcje wyrażenia regularnego <xref:System.Text.RegularExpressions> przestrzeni nazw. Można używać tych działań niestandardowych aplikacji przepływu pracy. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]wyrażenia regularne, zobacz [N:System.Text.RegularExpressions](http://go.microsoft.com/fwlink/?LinkId=150434) Namespace.  
  
 Poniższa tabela zawiera szczegóły dotyczące działania niestandardowe, w tym przykładzie.  
  
|Działanie|Opis|  
|--------------|-----------------|  
|IsMatch|Określa, czy wyrażenie regularne Znaleziono dopasowanie w ciągu wejściowym.|  
|Dopasowania|Wyszukuje ciąg wejściowy dla wszystkich wystąpień elementu wyrażenia regularnego i zwraca wszystkie dopasowania powiodło się.|  
|Zamień|W ramach określonego ciągu wejściowego zastępuje ciągi zgodne ze wzorcem wyrażenia regularnego z określony ciąg zastępczy.|  
  
## <a name="ismatch"></a>IsMatch  
 `IsMatch` Zwraca działania niestandardowego `true` Jeśli `Input` właściwości ciągu znalezieniu dopasowania z wyrażeniem regularnym określonym w `Pattern` właściwości. Działanie jest pochodną <xref:System.Activities.CodeActivity%601> i poziomu <xref:System.Activities.CodeActivity%601.Execute%2A> wywołania metody <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metody.  
  
 W poniższej tabeli opisano wartość właściwości i przywracać `IsMatch` działania niestandardowego.  
  
|Właściwości lub wartości zwracanej|Opis|  
|------------------------------|-----------------|  
|Wzorzec (wymagane)|Wyrażenie regularne do wyszukania z.|  
|Dane wejściowe (wymagane)|Wejściowy ciąg do wyszukania.|  
|RegexOptions|Bitowe połączenie lub [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) wartości wyliczenia.|  
|Wartość zwracana|`true`Jeśli dane wejściowe znalezienia dopasowania we wzorcu podana; w przeciwnym razie `false`.|  
  
 Poniższy przykład kodu pokazuje sposób użycia `IsMatch` działania niestandardowego.  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a>Dopasowania  
 `Matches` Działania niestandardowego wyszukuje ciąg wejściowy dla wszystkich wystąpień elementu wyrażenia regularnego i zwraca wszystkie dopasowania powiodło się. Działanie jest pochodną <xref:System.Activities.CodeActivity%601> i poziomu <xref:System.Activities.CodeActivity%601.Execute%2A> wywołania metody <xref:System.Text.RegularExpressions.Regex.Matches%2A> metody.  
  
 W poniższej tabeli opisano wartość właściwości i przywracać `IsMatch` działania niestandardowego.  
  
|Właściwości lub wartości zwracanej|Opis|  
|------------------------------|-----------------|  
|Wzorzec (wymagane)|Wyrażenie regularne do wyszukania z.|  
|Dane wejściowe (wymagane)|Wejściowy ciąg do wyszukania.|  
|RegexOptions|Bitowe połączenie lub [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) wartości wyliczenia.|  
|Wartość zwracana|A <xref:System.Text.RegularExpressions.MatchCollection> zawierający kolekcja dopasowań powiodło się.|  
  
 Poniższy przykład kodu pokazuje sposób użycia `Matches` działania niestandardowego.  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a>Zamień  
 `Replace` Działania niestandardowego wyszukuje ciąg wejściowy i zastępuje wszystkie ciągi, które pasują do podanego wyrażenia regularnego z ciągiem. Działanie jest pochodną <xref:System.Activities.CodeActivity%601> i poziomu <xref:System.Activities.CodeActivity%601.Execute%2A> wywołania metody <xref:System.Text.RegularExpressions.Regex.Replace%2A> metody.  
  
 W poniższej tabeli opisano wartość właściwości i przywracać `Replace` działania niestandardowego.  
  
|Właściwości lub wartości zwracanej|Opis|  
|------------------------------|-----------------|  
|Wzorzec (wymagane)|Wyrażenie regularne do wyszukania z.|  
|Dane wejściowe (wymagane)|Wejściowy ciąg do wyszukania.|  
|Zastąpienie|Ciąg zastępujący.<br /><br /> Jeśli `Replacement` jest określony, a następnie `MatchEvaluator` właściwość jest ignorowana. Albo `Replacement` lub `MatchEvaluator` musi być ustawiona właściwość.|  
|MatchEvaluator|Niestandardowe metody, która sprawdza każdym dopasowaniu i zwraca oryginalnego ciągu dopasowane lub ciąg zastępczy.<br /><br /> Jeśli `Replacement` jest określony, a następnie `MatchEvaluator` właściwość jest ignorowana. Albo `Replacement` lub `MatchEvaluator` musi być ustawiona właściwość.|  
|RegexOptions|Bitowe połączenie lub [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) wartości wyliczenia.|  
|Wartość zwracana|A <xref:System.Text.RegularExpressions.MatchCollection> zawierający kolekcja dopasowań powiodło się.|  
  
 Poniższy przykład kodu pokazuje sposób użycia `Replace` działania niestandardowego.  
  
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
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania RegexActivities.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`