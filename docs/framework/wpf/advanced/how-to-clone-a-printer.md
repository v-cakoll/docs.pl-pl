---
title: Jak sklonować drukarkę
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
ms.openlocfilehash: 8f3a9c3b4d9f4bcbe3a6ffcff9868aa7b19b8f28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544206"
---
# <a name="how-to-clone-a-printer"></a>Jak sklonować drukarkę
Większość firm będzie w pewnym momencie zakupu wiele drukarek tego samego modelu. Zazwyczaj te są wszystkie zainstalowane przy użyciu ustawień konfiguracyjnych niemal identyczne. Instalowanie poszczególnych drukarek może być czasochłonne i podatne na błąd. <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> Przestrzeni nazw i <xref:System.Printing.PrintServer.InstallPrintQueue%2A> klasy, które są dostępne z programu Microsoft .NET Framework umożliwia teraz instalować dowolną liczbę kolejek wydruku dodatkowe, które są klonowane z istniejącej kolejki wydruku.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie drugi kolejki wydruku został sklonowany z istniejącej kolejki wydruku. Drugi różni się od pierwszego tylko w jego nazwę, lokalizacji, port i stanu udostępnionego. Oto główne kroki w ten sposób.  
  
1.  Utwórz <xref:System.Printing.PrintQueue> obiektu dla istniejącej drukarki, która ma zostać sklonowany.  
  
2.  Utwórz <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> z <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> z <xref:System.Printing.PrintQueue>. <xref:System.Collections.DictionaryEntry.Value%2A> Właściwości każdego wpisu w tym słowniku jest obiektem jednego z jego typów pochodnych <xref:System.Printing.IndexedProperties.PrintProperty>. Istnieją dwa sposoby ustawiania wartości wpisu w tym słowniku.  
  
    -   Użyj słownika **Usuń** i <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> metody Usuń wpis, a następnie dodaj go ponownie z żądaną wartość.  
  
    -   Użyj słownika <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> metody.  
  
     W poniższym przykładzie przedstawiono w obu kierunkach.  
  
3.  Utwórz <xref:System.Printing.IndexedProperties.PrintBooleanProperty> obiektu i ustawić jej <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> do "IsShared" i jego <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> do `true`.  
  
4.  Użyj <xref:System.Printing.IndexedProperties.PrintBooleanProperty> była wartość <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>dla wpisu "IsShared".  
  
5.  Utwórz <xref:System.Printing.IndexedProperties.PrintStringProperty> obiektu i ustawić jej <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> do "ShareName" i jego <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> do odpowiedniej <xref:System.String>.  
  
6.  Użyj <xref:System.Printing.IndexedProperties.PrintStringProperty> była wartość <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>jego wpis "ShareName".  
  
7.  Utworzyć inną <xref:System.Printing.IndexedProperties.PrintStringProperty> obiektu i ustawić jej <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> do "Lokalizacja" i jego <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> do odpowiedniej <xref:System.String>.  
  
8.  Użyj drugi <xref:System.Printing.IndexedProperties.PrintStringProperty> była wartość <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>jego wpis "Lokalizacja".  
  
9. Utwórz tablicę <xref:System.String>s. Każdy element jest to nazwa portu na serwerze.  
  
10. Użyj <xref:System.Printing.PrintServer.InstallPrintQueue%2A> do zainstalowania nowej drukarki przy użyciu nowych wartości.  
  
 Przykładem jest poniżej.  
  
 [!code-csharp[ClonePrinter#ClonePrinter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [Dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Przegląd drukowania](../../../../docs/framework/wpf/advanced/printing-overview.md)
