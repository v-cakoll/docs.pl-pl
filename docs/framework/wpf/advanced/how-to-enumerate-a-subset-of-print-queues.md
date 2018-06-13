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
ms.openlocfilehash: 3e616b3b61b4b1b561d5bdb7e51525f391901a22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543592"
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a>Jak wykazać podzbiór kolejek drukowania
Typowe sytuacji przez specjalistów technologii informatycznych (IT) Zarządzanie zbiór drukarki w firmie, które muszą ponieść polega na generowaniu listę drukarek posiadające niektórych właściwości. Ta funkcja jest zapewniana przez <xref:System.Printing.PrintServer.GetPrintQueues%2A> metody <xref:System.Printing.PrintServer> obiektu i <xref:System.Printing.EnumeratedPrintQueueTypes> wyliczenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu rozpoczyna się od utworzenia tablicy flagi określające właściwości kolejki wydruku, którą chcemy, aby wyświetlić listę. W tym przykładzie czekamy dla kolejek drukowania, które są instalowane lokalnie na serwerze wydruku i są współdzielone. <xref:System.Printing.EnumeratedPrintQueueTypes> Wyliczenie zawiera wiele innych możliwości.  
  
 Następnie tworzony <xref:System.Printing.LocalPrintServer> obiektu, klasą pochodną <xref:System.Printing.PrintServer>. Lokalny serwer wydruku jest komputer, na którym jest uruchomiona aplikacja.  
  
 Ostatni krok istotne jest przekazanie tablicy, tak aby <xref:System.Printing.PrintServer.GetPrintQueues%2A> metody.  
  
 Na koniec wyniki są prezentowane użytkownikowi.  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 W tym przykładzie można rozszerzyć przez `foreach` pętli, które kroki do każdej kolejki wydruku przeprowadzić dalszą kontroli. Na przykład użytkownik może odfiltrowania drukarki, które nie obsługują drukowania dwustronnego przez wywołanie pętli każdej kolejki wydruku <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> — metoda i testowania zwrócona wartość obecność dupleksu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [Dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Przegląd drukowania](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Moduł zapisywania dokumentów XPS firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=147319)
