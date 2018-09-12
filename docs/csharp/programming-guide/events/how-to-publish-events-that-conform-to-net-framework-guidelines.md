---
title: 'Porady: publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi .NET Framework (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 9a17aaec20b03325abadfcc168f7ac4653f300df
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44514595"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>Porady: publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi .NET Framework (Przewodnik programowania w języku C#)
W poniższej procedurze przedstawiono sposób dodawania zdarzenia, które są zgodne ze standardem [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] wzorzec do klas i struktur. Wszystkie zdarzenia w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] biblioteki klas są oparte na <xref:System.EventHandler> delegować, która została zdefiniowana w następujący sposób:  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] Wprowadza ogólnego wersji tego obiektu delegowanego <xref:System.EventHandler%601>. Następujące przykłady przedstawiają sposób użycia obu wersji.  
  
 Mimo że zdarzeń w klasach, które definiujesz może bazować na dowolnego typu delegata prawidłowe nawet obiektów delegowanych, które zwracają wartość, ogólnie zaleca się na podstawie zdarzeń [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] wzorca za pomocą <xref:System.EventHandler>, jak pokazano w poniższym przykładzie.  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>Do publikowania zdarzeń oparta na wzorcu EventHandler  
  
1.  (Pomiń ten krok i przejdź do kroku 3a, jeśli nie masz do wysyłania niestandardowych danych za pomocą zdarzenia). Deklarowanie klasy dla niestandardowych danych w zakresie, który jest widoczny dla obu wydawcy i subskrybenta klasy. Następnie dodaj wymagane elementy członkowskie do przechowywania danych zdarzenia niestandardowego. W tym przykładzie zwracany jest prosty ciąg.  
  
    ```csharp  
    public class CustomEventArgs : EventArgs  
    {  
        public CustomEventArgs(string s)  
        {  
            msg = s;  
        }  
        private string msg;  
        public string Message  
        {  
            get { return msg; }  
        }   
    }  
    ```  
  
2.  (Pomiń ten krok, jeśli używasz wersji ogólnych <xref:System.EventHandler%601> .) Należy zadeklarować delegata w klasie publikowania. Nadaj mu nazwę, która kończy się *EventHandler*. Drugi parametr określa swój niestandardowy typ EventArgs.  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3.  Zadeklaruj zdarzenie w klasie publikacji przy użyciu jednej z następujących czynności.  
  
    1.  Jeśli nie masz żadnych niestandardowej klasy EventArgs, typu zdarzenia będą delegata EventHandler nieogólnego. Nie trzeba zadeklarować obiektu delegowanego, ponieważ jest już zadeklarowana w <xref:System> przestrzeni nazw, która jest dołączana w przypadku utworzenia projektu języka C#. Dodaj następujący kod do klasy wydawcy.  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2.  Jeśli używasz wersji nieogólnego <xref:System.EventHandler> i masz niestandardowej klasy pochodzącej od <xref:System.EventArgs>zadeklarować zdarzenia wewnątrz klasy publikowania i używanie swoim delegacie z kroku 2 jako typu.  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3.  Jeśli używasz wersji ogólnego, nie trzeba niestandardową klasę delegatów. Zamiast tego, w klasie publikacji, należy określić typu zdarzenia jako `EventHandler<CustomEventArgs>`, zastępując nazwę klasy między nawiasami.  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano poprzednich krokach za pomocą niestandardowej klasy EventArgs i <xref:System.EventHandler%601> jako typ zdarzenia.  
  
 [!code-csharp[csProgGuideEvents#2](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-publish-events-that-conform-to-net-framework-guidelines_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Delegate>  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
- [Delegaci](../../../csharp/programming-guide/delegates/index.md)
