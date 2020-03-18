---
title: Jak publikować zdarzenia zgodne z wytycznymi programu .NET Framework — Przewodnik po programowaniu języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 90c079b9f7dbf2a1d963b7eee4447145d7a10432
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167540"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>Jak publikować zdarzenia zgodne z wytycznymi programu .NET Framework (Przewodnik programowania c#)
W poniższej procedurze przedstawiono sposób dodawania zdarzeń, które postępują zgodnie ze standardowym wzorcem .NET Framework do klas i struktur. Wszystkie zdarzenia w bibliotece klas .NET <xref:System.EventHandler> Framework są oparte na pełnomocniku, który jest zdefiniowany w następujący sposób:  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
> .NET Framework 2.0 wprowadza ogólną wersję tego <xref:System.EventHandler%601>delegata. W poniższych przykładach przedstawiono sposób używania obu wersji.  
  
 Mimo że zdarzenia w klasach, które można zdefiniować może być oparta na dowolny prawidłowy typ delegata, nawet delegatów, <xref:System.EventHandler>które zwracają wartość, ogólnie zaleca się, aby oprzeć zdarzenia na wzorcu .NET Framework przy użyciu , jak pokazano w poniższym przykładzie.  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>Aby opublikować zdarzenia na podstawie wzorca EventHandler  
  
1. (Pomiń ten krok i przejdź do kroku 3a, jeśli nie musisz wysyłać niestandardowych danych ze zdarzeniem). Zadeklarować klasę dla danych niestandardowych w zakresie, który jest widoczny zarówno dla wydawcy i klasy subskrybenta. Następnie dodaj wymaganych członków do przechowywania danych zdarzeń niestandardowych. W tym przykładzie zwracany jest prosty ciąg.  
  
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
  
2. (Pomiń ten krok, jeśli <xref:System.EventHandler%601> używasz ogólnej wersji .) Deklaruj pełnomocnika w klasie publikowania. Nadaj mu nazwę, która kończy się *eventhandler*. Drugi parametr określa niestandardowy typ EventArgs.  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3. Zadeklaruj zdarzenie w klasie publikowania, wykonując jedną z następujących czynności.  
  
    1. Jeśli nie masz niestandardowej klasy EventArgs, typ zdarzenia będzie nierodzajowym delegatem EventHandler. Nie trzeba zadeklarować delegata, ponieważ jest już <xref:System> zadeklarowany w obszarze nazw, który jest uwzględniony podczas tworzenia projektu C#. Dodaj następujący kod do klasy wydawcy.  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2. Jeśli używasz wersji nierodzajowej <xref:System.EventHandler> i masz klasę niestandardową <xref:System.EventArgs>wywodzącą się z , zadeklarować zdarzenie wewnątrz klasy publikowania i używać delegata z kroku 2 jako typ.  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3. Jeśli używasz wersji ogólnej, nie potrzebujesz delegata niestandardowego. Zamiast tego w klasie publikowania należy `EventHandler<CustomEventArgs>`określić typ zdarzenia jako zastępując nazwę własnej klasy między nawiasami kąta.  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono poprzednie kroki przy użyciu <xref:System.EventHandler%601> niestandardowej klasy EventArgs i jako typ zdarzenia.  
  
 [!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Delegate>
- [Przewodnik programowania języka C#](../index.md)
- [Zdarzenia](./index.md)
- [Delegaty](../delegates/index.md)
