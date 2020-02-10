---
title: Jak wykazać podzbiór kolejek drukowania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
ms.openlocfilehash: aae41931f012f6d34fc057fdd6ee9fc9baab6e7b
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094543"
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a>Jak wykazać podzbiór kolejek drukowania
Powszechną sytuacją, jaką specjaliści z technologią informatyczną (IT) do zarządzania zestawem drukarek w całej firmie jest generowanie listy drukarek mających pewne cechy. Ta funkcja jest udostępniana przez metodę <xref:System.Printing.PrintServer.GetPrintQueues%2A> obiektu <xref:System.Printing.PrintServer> i wyliczenia <xref:System.Printing.EnumeratedPrintQueueTypes>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kod rozpoczyna się od utworzenia tablicy flag, które określają charakterystyki kolejek wydruku, które chcemy wyświetlić. W tym przykładzie szukasz kolejek wydruku zainstalowanych lokalnie na serwerze wydruku i są one udostępnione. Wyliczenie <xref:System.Printing.EnumeratedPrintQueueTypes> zapewnia wiele innych możliwości.  
  
 Następnie kod tworzy obiekt <xref:System.Printing.LocalPrintServer>, klasy pochodnej z <xref:System.Printing.PrintServer>. Lokalny serwer wydruku to komputer, na którym działa aplikacja.  
  
 Ostatni znaczący krok polega na przejściu tablicy do metody <xref:System.Printing.PrintServer.GetPrintQueues%2A>.  
  
 Na koniec wyniki są prezentowane użytkownikowi.  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 Możesz rozszerzyć ten przykład, wykonując pętlę `foreach`, która przechodzi przez każdą kolejkę wydruku w celu dalszej kontroli. Na przykład można wypróbować drukarki, które nie obsługują drukowania dwustronnego, ponieważ pętla wywołuje każdą metodę <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> kolejki wydruku i testuje zwracaną wartość dla obecności dupleksu.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [Dokumenty w WPF](documents-in-wpf.md)
- [Przegląd drukowania](printing-overview.md)
- [Moduł zapisywania dokumentów XPS firmy Microsoft](/windows/win32/printdocs/microsoft-xps-document-writer)
