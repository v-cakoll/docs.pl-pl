---
title: 'Instrukcje: Klonowanie drukarki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- print queues [WPF]
- cloning printers [WPF]
- printers [WPF], cloning
- print queues [WPF], cloning
- cloning print queues [WPF]
ms.assetid: dd6997c9-fe04-40f8-88a6-92e3ac0889eb
ms.openlocfilehash: 09a445da068f0141b9526e0228df8be0105498c6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310463"
---
# <a name="how-to-clone-a-printer"></a>Instrukcje: Klonowanie drukarki
Większość firm w pewnym momencie kupić wiele drukarek tego samego modelu. Zazwyczaj te wszystkie są instalowane przy użyciu ustawień konfiguracyjnych niemal identyczne. Instalowanie poszczególnych drukarki może być czasochłonne i podatne. <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> Przestrzeni nazw i <xref:System.Printing.PrintServer.InstallPrintQueue%2A> klasy, które są udostępniane za pomocą programu Microsoft .NET Framework umożliwia natychmiastowe zainstalować dowolną liczbę dodatkowych kolejek drukowania, które są klonowane z istniejącej kolejki wydruku.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie druga kolejki wydruku został sklonowany z istniejącej kolejki wydruku. Drugi różni się od pierwszego tylko w przypadku nazwy, lokalizacji, port i udostępniony stan. Oto główne kroki w ten sposób.  
  
1. Utwórz <xref:System.Printing.PrintQueue> obiektu dla istniejącej drukarki, która ma być klonowane.  
  
2. Tworzenie <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> z <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> z <xref:System.Printing.PrintQueue>. <xref:System.Collections.DictionaryEntry.Value%2A> Właściwości każdego wpisu, w tym słowniku jest obiektem, jednego z typów pochodnych typu <xref:System.Printing.IndexedProperties.PrintProperty>. Istnieją dwa sposoby, aby ustawić wartość wpisu w tym słowniku.  
  
    -   Użyj słownika **Usuń** i <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> metody Usuń wpis, a następnie dodaj go ponownie z wymaganą wartość.  
  
    -   Użyj słownika <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> metody.  
  
     W poniższym przykładzie przedstawiono w obu kierunkach.  
  
3. Tworzenie <xref:System.Printing.IndexedProperties.PrintBooleanProperty> obiektu i ustaw jego <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> do "IsShared" i jego <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> do `true`.  
  
4. Użyj <xref:System.Printing.IndexedProperties.PrintBooleanProperty> obiektu jako wartość <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>firmy wpis "IsShared".  
  
5. Tworzenie <xref:System.Printing.IndexedProperties.PrintStringProperty> obiektu i ustaw jego <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> do "Nazwa_udziału" i jego <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> do odpowiedniej <xref:System.String>.  
  
6. Użyj <xref:System.Printing.IndexedProperties.PrintStringProperty> obiektu jako wartość <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>firmy wpis "Nazwa_udziału".  
  
7. Utworzyć kolejną <xref:System.Printing.IndexedProperties.PrintStringProperty> obiektu i ustaw jego <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> do "Lokalizacja" i jego <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> do odpowiedniej <xref:System.String>.  
  
8. Drugą <xref:System.Printing.IndexedProperties.PrintStringProperty> obiektu jako wartość <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>firmy wpis "Lokalizacja".  
  
9. Utwórz tablicę <xref:System.String>s. Każdy element jest nazwa portu na serwerze.  
  
10. Użyj <xref:System.Printing.PrintServer.InstallPrintQueue%2A> do zainstalowania nowej drukarki z nowymi wartościami.  
  
 Przykład znajduje się poniżej.  
  
 [!code-csharp[ClonePrinter#ClonePrinter](~/samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Printing.IndexedProperties>
- <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.PrintQueue>
- <xref:System.Collections.DictionaryEntry>
- [Dokumenty w WPF](documents-in-wpf.md)
- [Przegląd drukowania](printing-overview.md)
