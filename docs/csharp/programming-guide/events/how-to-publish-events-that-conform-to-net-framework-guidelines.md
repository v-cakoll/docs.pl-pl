---
title: Jak opublikować zdarzenia zgodne z wytycznymi .NET Framework — Przewodnik programowania w języku C#
ms.date: 05/26/2020
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 137e52b80703491a4528a3eddc7fa12f9dce6f52
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144802"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>Jak opublikować zdarzenia zgodne z zaleceniami .NET Framework (Przewodnik programowania w języku C#)

Poniższa procedura pokazuje, jak dodać zdarzenia, które obserwują standardowy wzorzec .NET Framework do klas i struktur. Wszystkie zdarzenia w bibliotece klas .NET Framework są oparte na <xref:System.EventHandler> delegatze, który jest zdefiniowany w następujący sposób:

```csharp
public delegate void EventHandler(object sender, EventArgs e);
```

> [!NOTE]
> W .NET Framework 2,0 wprowadzono ogólną wersję tego delegata <xref:System.EventHandler%601> . W poniższych przykładach pokazano, jak używać obu wersji.

Chociaż zdarzenia w zdefiniowanych klasach mogą opierać się na dowolnym prawidłowym typie delegata, nawet delegatów zwracających wartość, zazwyczaj zaleca się oparcie zdarzeń na wzorcu .NET Framework przy użyciu <xref:System.EventHandler> , jak pokazano w poniższym przykładzie.

Nazwa `EventHandler` może prowadzić do nieprawidłowych pomyłek, ponieważ nie jest w rzeczywistości obsługiwana dla zdarzenia. <xref:System.EventHandler>, I ogólne <xref:System.EventHandler%601> są typami delegatów. Metoda lub wyrażenie lambda, którego sygnatura jest zgodna z definicją delegata, jest *obsługą zdarzeń* i zostanie wywołana, gdy zdarzenie zostanie zgłoszone.

### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>Aby opublikować zdarzenia na podstawie wzorca EventHandler

1. (Pomiń ten krok i przejdź do kroku 3a, jeśli nie musisz wysyłać niestandardowych danych do zdarzenia). Zadeklaruj klasę niestandardowych danych w zakresie, który jest widoczny dla obu klas wydawcy i subskrybenta. Następnie Dodaj wymagane elementy członkowskie, aby przechowywać dane niestandardowego zdarzenia. W tym przykładzie jest zwracany prosty ciąg.

    ```csharp
    public class CustomEventArgs : EventArgs
    {
        public CustomEventArgs(string message)
        {
            Message = message;
        }

        public string Message { get; set; }
    }
    ```

2. (Pomiń ten krok, jeśli używasz ogólnej wersji programu <xref:System.EventHandler%601> ). Zadeklaruj delegat w klasie publikacji. Nadaj jej nazwę kończącą się na `EventHandler` . Drugi parametr określa `EventArgs` typ niestandardowy.

    ```csharp
    public delegate void CustomEventHandler(object sender, CustomEventArgs args);
    ```

3. Zadeklaruj zdarzenie w klasie publikacji przy użyciu jednego z następujących kroków.

    1. Jeśli nie masz niestandardowej klasy EventArgs, typ zdarzenia będzie nieogólnym delegatem EventHandler. Nie trzeba deklarować delegata, ponieważ jest on już zadeklarowany w <xref:System> przestrzeni nazw, która jest uwzględniona podczas tworzenia projektu w języku C#. Dodaj następujący kod do klasy wydawcy.

        ```csharp
        public event EventHandler RaiseCustomEvent;
        ```

    2. Jeśli używasz nieogólnej wersji programu <xref:System.EventHandler> i masz klasę niestandardową pochodną od <xref:System.EventArgs> , zadeklaruj zdarzenie wewnątrz klasy publikacji i użyj delegata z kroku 2 jako typ.

        ```csharp
        public event CustomEventHandler RaiseCustomEvent;
        ```

    3. Jeśli używasz wersji ogólnej, nie potrzebujesz niestandardowego delegata. Zamiast tego w klasie publikacji należy określić typ zdarzenia jako `EventHandler<CustomEventArgs>` , zastępując nazwę własnej klasy między nawiasami kątowymi.

        ```csharp
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;
        ```

## <a name="example"></a>Przykład

Poniższy przykład demonstruje poprzednie kroki przy użyciu niestandardowej klasy EventArgs i <xref:System.EventHandler%601> jako typ zdarzenia.

[!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Delegate>
- [Przewodnik programowania w języku C#](../index.md)
- [Zdarzenia](index.md)
- [Delegaci](../delegates/index.md)
