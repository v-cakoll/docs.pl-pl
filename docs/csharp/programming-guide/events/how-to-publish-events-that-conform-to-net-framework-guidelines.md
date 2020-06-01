---
title: Publikuj zdarzenia zgodne z zaleceniami platformy .NET — Przewodnik programowania w języku C#
ms.date: 05/26/2020
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: df2f643f867b93b74d04d8fbd673df545c28938e
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240749"
---
# <a name="how-to-publish-events-that-conform-to-net-guidelines-c-programming-guide"></a>Jak opublikować zdarzenia zgodne z zaleceniami dotyczącymi platformy .NET (Przewodnik programowania w języku C#)

Poniższa procedura pokazuje, jak dodać zdarzenia zgodne ze standardowym wzorcem .NET do klas i struktur. Wszystkie zdarzenia w bibliotece klas .NET Framework są oparte na <xref:System.EventHandler> delegatze, który jest zdefiniowany w następujący sposób:

```csharp
public delegate void EventHandler(object sender, EventArgs e);
```

> [!NOTE]
> .NET Framework 2,0 wprowadza ogólną wersję tego delegata, <xref:System.EventHandler%601> . W poniższych przykładach pokazano, jak używać obu wersji.

Chociaż zdarzenia w zdefiniowanych klasach mogą opierać się na dowolnym prawidłowym typie delegata, nawet delegatów zwracających wartość, zazwyczaj zaleca się oparcie zdarzeń na wzorcu .NET przy użyciu <xref:System.EventHandler> , jak pokazano w poniższym przykładzie.

Nazwa `EventHandler` może prowadzić do nieprawidłowych pomyłek, ponieważ nie jest w rzeczywistości obsługiwana dla zdarzenia. <xref:System.EventHandler>, I ogólne <xref:System.EventHandler%601> są typami delegatów. Metoda lub wyrażenie lambda, którego sygnatura jest zgodna z definicją delegata, jest *obsługą zdarzeń* i zostanie wywołana, gdy zdarzenie zostanie zgłoszone.

## <a name="publish-events-based-on-the-eventhandler-pattern"></a>Publikuj zdarzenia na podstawie wzorca EventHandler

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

## <a name="see-also"></a>Zobacz też

- <xref:System.Delegate>
- [Przewodnik programowania w języku C#](../index.md)
- [Zdarzenia](index.md)
- [Delegaci](../delegates/index.md)
