---
title: 'Porady: publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi .NET Framework (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 830f86be43f1499bd87ff02690061b08f8f7f86d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322640"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>Porady: publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi .NET Framework (Przewodnik programowania w języku C#)
W poniższej procedurze przedstawiono sposób dodawania zdarzenia, które są zgodne ze standardem [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] wzorzec do klas i struktur. Wszystkie zdarzenia w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] biblioteki klas są oparte na <xref:System.EventHandler> delegata, która jest zdefiniowana w następujący sposób:  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] Przedstawiono ogólny wersji tego obiektu delegowanego <xref:System.EventHandler%601>. Następujące przykłady przedstawiają sposób użycia obie wersje.  
  
 Mimo że zdarzeń w klasach zdefiniowanych przez użytkownika może być oparta na dowolnego typu delegata prawidłowe nawet pełnomocników, które zwracają wartości, jest zwykle zalecane na podstawie zdarzeń [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] wzorca za pomocą <xref:System.EventHandler>, jak pokazano w poniższym przykładzie.  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>Aby opublikować zdarzenia oparte na wzorcu EventHandler  
  
1.  (Pomiń ten krok i przejdź do kroku 3a, jeśli nie masz do wysyłania danych niestandardowych z wydarzenia). Zadeklarować klasy w niestandardowych danych w zakresie, widocznego dla obu wydawcy i subskrybenta klasy. Następnie dodaj członków wymagane do przechowywania danych zdarzenia niestandardowego. W tym przykładzie zostanie zwrócony ciąg proste.  
  
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
  
2.  (Ten krok można pominąć, jeśli używasz wersji ogólnego <xref:System.EventHandler%601> .) Zadeklarować obiektu delegowanego w klasie publikowania. Nadaj nazwę, która kończy się *EventHandler*. Drugi parametr określa typ EventArgs swojego niestandardowych.  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3.  Deklarowanie zdarzenia w klasie publikowania za pomocą jednej z następujących czynności.  
  
    1.  Jeśli masz nie niestandardowej klasy EventArgs danego typu zdarzenia będą delegata EventHandler nierodzajową. Nie należy deklarować delegata, ponieważ jest już zadeklarowany w <xref:System> przestrzeni nazw, która jest dołączana w przypadku tworzenia projektu C#. Dodaj następujący kod do klasy wydawcy.  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2.  Jeśli używasz wersji nieogólnego <xref:System.EventHandler> i mieć niestandardowej klasy pochodzącej od <xref:System.EventArgs>, zadeklarować wydarzenia w klasie publikowania i używana jako typ pełnomocnika w kroku 2.  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3.  Jeśli używasz wersji ogólnego, nie trzeba niestandardowego obiektu delegowanego. Zamiast tego w klasie publikowania, musisz wybrać typ użytkownika zdarzeń jako `EventHandler<CustomEventArgs>`, zastępując nazwę klasy między nawiasami.  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano poprzednich kroków za pomocą niestandardowej klasy EventArgs i <xref:System.EventHandler%601> jako typ zdarzenia.  
  
 [!code-csharp[csProgGuideEvents#2](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-publish-events-that-conform-to-net-framework-guidelines_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Delegate>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
 [Delegaci](../../../csharp/programming-guide/delegates/index.md)
