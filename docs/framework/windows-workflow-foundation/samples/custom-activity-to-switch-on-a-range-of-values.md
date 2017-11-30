---
title: "Działań niestandardowych do przełącznika na zakres wartości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 441e0a17-421f-430c-ba97-59e4cc6c88e3
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ff6a55157e886b54d631d1ca5d2598785de7608d
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="custom-activity-to-switch-on-a-range-of-values"></a>Działań niestandardowych do przełącznika na zakres wartości
Ten przykład przedstawia sposób tworzenia działań niestandardowych, rozszerzający stosowania <xref:System.Activities.Statements.Switch%601>. Konwencjonalne <xref:System.Activities.Statements.Switch%601> instrukcji umożliwia przełączanie oparte na pojedynczej wartości. Istnieją jednak biznesowych, które scenariuszy, w którym działanie, musisz przełączyć ustalane na podstawie zakresu wartości. Na przykład działanie może wykonać jedno działanie, gdy jest przełączany na wartość od 1 do 5, innej akcji, gdy wartość jest od 6 do 10 i domyślnego działania dla wszystkich innych wartości. To niestandardowe działanie umożliwia dokładnie tego scenariusza.  
  
## <a name="the-switchrange-activity"></a>Działanie SwitchRange  
 `SwitchRange` Działania planuje działaniem podrzędnym, gdy wartość wyniku jej wyrażenia znajduje się w zakresie jednej z jego `Cases`.  
  
 Następujący przykładowy kod to niestandardowe działanie, które przełączniki ustalane na podstawie zakresu wartości.  
  
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
|Wyrażenie|Jest to wyrażenie, które ma zostać obliczone i porównywana zakresów na liście przypadków. Wynikiem wyrażenia jest typu T.|  
|Przypadków|Każdej sprawy składa się z zakresu (od a do) i działania (jednostka). Wyrażenie jest obliczane i porównywana zakresów. Jeśli wynikiem wyrażenia jest spoza zakresu przypadków, odpowiadające mu działanie jest wykonywana.|  
|Domyślny|Działanie, które jest wykonywane, gdy w żadnym przypadku nie odpowiada. Jeśli wartość `null`, nie podjęto żadnej akcji.|  
  
## <a name="caserange-class"></a>Klasa CaseRange  
 `CaseRange` Klasa reprezentuje zakresem w ramach `SwitchRange` działania. Każde wystąpienie `CaseRange` zawiera zakres (składający się z `From` i `To`) i `Body` działanie, które jest zaplanowane, jeśli wyrażenie w `SwitchRange` jest obliczane w zakresie.  
  
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
>  Zarówno `SwitchRange` i `CaseRange` klasy, które są zdefiniowane w próbce są klas ogólnych, które mogą pracować z dowolnego typu, który implementuje `IComparable`, takiej jak <xref:System.Activities.Statements.Switch%601> klasy.  
  
## <a name="sample-usage"></a>Przykładowe zastosowanie  
 Poniższy przykład kodu pokazuje sposób użycia `SwitchRange` działania.  
  
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
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania SwitchRange.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SwitchRange`