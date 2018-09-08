---
title: Działanie niestandardowe do przełączania na zakres wartości
ms.date: 03/30/2017
ms.assetid: 441e0a17-421f-430c-ba97-59e4cc6c88e3
ms.openlocfilehash: cfaf4318b1557a9fc217de8254e164243ea54569
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195309"
---
# <a name="custom-activity-to-switch-on-a-range-of-values"></a>Działanie niestandardowe do przełączania na zakres wartości
W tym przykładzie pokazano, jak utworzyć niestandardowe działanie, która rozszerza użytkowania <xref:System.Activities.Statements.Switch%601>. Konwencjonalne <xref:System.Activities.Statements.Switch%601> instrukcji umożliwia przełączanie oparte na pojedynczej wartości. Istnieją jednak biznesowych, które scenariusze, w którym działanie, musisz przełączyć na podstawie zakresu wartości. Na przykład działanie może być wykonywany jedną akcję, gdy przełączany na wartość od 1 do 5, innej akcji, gdy wartość jest równa od 6 do 10 i domyślna akcja dla wszystkich pozostałych wartości. To niestandardowe działanie umożliwia dokładnie tego scenariusza.  
  
## <a name="the-switchrange-activity"></a>Działanie SwitchRange  
 `SwitchRange` Działania planuje działania podrzędnego, gdy wartość wyniku jej wyrażenia jest uwzględnione w zakresie jednej z jego `Cases`.  
  
 Poniższy przykład kodu jest niestandardowe działanie, które przełączniki na podstawie zakresu wartości.  
  
```csharp  
public sealed class SwitchRange<T> : NativeActivity where T : IComparable  
{  
   [RequiredArgument]  
   [DefaultValue(null)]  
   public InArgument<T> Expression { get; set; }  
  
   public IList<CaseRange<T>> Cases  
  
   [DefaultValue(null)]  
   public Activity Default { get; set; }}  
}  
```  
  
|Właściwość|Opis|  
|-|-|  
|Wyrażenie|To wyrażenie, które ma zostać obliczone i porównywana zakresów na liście przypadków. Wynikiem wyrażenia jest typu T.|  
|Przypadków|Każdy przypadek składa się z zakresu (od a do) i działania (treść). Wyrażenie jest obliczane i porównywana z zakresów. Jeśli wynikiem wyrażenia jest w zakresie przypadkach, odpowiadające mu działanie jest wykonywana.|  
|Domyślny|Działanie, które jest wykonywany, gdy żaden przypadek nie jest dopasowany. Po ustawieniu `null`, nie podjęto żadnej akcji.|  
  
## <a name="caserange-class"></a>Klasa CaseRange  
 `CaseRange` Klasa reprezentuje zakres, w ramach `SwitchRange` działania. Każde wystąpienie `CaseRange` zawiera zakres (składające się z `From` i `To`) i `Body` działania, które jest zaplanowane, jeśli wyrażenie w `SwitchRange` jest szacowana w ramach zakresu.  
  
 Poniższy przykład kodu jest definicja `CaseRange` klasy.  
  
```  
public class CaseRange<T> where T : IComparable  
{  
    public T From { get; set; }  
  
    public T To { get; set; }  
  
    public Activity Action { get; set; }  
}  
```  
  
> [!NOTE]
>  Zarówno `SwitchRange` i `CaseRange` klasy, które są zdefiniowane w przykładzie są klas ogólnych, które można pracować z dowolnego typu, który implementuje `IComparable`, takiej jak <xref:System.Activities.Statements.Switch%601> klasy.  
  
## <a name="sample-usage"></a>Przykładowe zastosowanie  
 Poniższy przykład kodu demonstruje sposób używania `SwitchRange` działania.  
  
```csharp  
Activity SwitchRange = new SwitchRange<int>  
{  
    Expression = new InArgument<int>(value),  
    Cases =   
    {  
        new CaseRange<int>                      
        {  
            From = 1,  
            To = 5,  
            Action = new WriteLine  
            {  
                Text = "Case 1-5 selected",  
            }  
        },  
        new CaseRange<int>  
        {  
            From = 6,  
            To = 10,  
            Action = new WriteLine  
            {  
                Text = "Case 6-10 selected",  
            }  
        }  
    },  
    Default = new WriteLine { Text = "Default Case selected" }  
};  
```  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania SwitchRange.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SwitchRange`