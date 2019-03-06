---
title: 'Instrukcje: Pobierz właściwości obiektu systemowego drukowania bez odbicia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
ms.openlocfilehash: b03be30422a93980ecdbcdbd428600fd41abd824
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367586"
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a>Instrukcje: Pobierz właściwości obiektu systemowego drukowania bez odbicia
Pozycjonuj właściwości (i typy tych właściwości) dla obiektu przy użyciu odbicia może zmniejszyć wydajność aplikacji. <xref:System.Printing.IndexedProperties> Przestrzeń nazw umożliwia pobranie tych informacji przy użyciu odbicia.  
  
## <a name="example"></a>Przykład  
 Dostępne są następujące kroki w ten sposób.  
  
1.  Utwórz wystąpienie tego typu. W poniższym przykładzie typ jest <xref:System.Printing.PrintQueue> typ, który jest dostarczany z programem Microsoft .NET Framework, ale prawie identyczna kodu powinny działać dla typów wyprowadzonych z <xref:System.Printing.PrintSystemObject>.  
  
2.  Tworzenie <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> z typu <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>. <xref:System.Collections.DictionaryEntry.Value%2A> Właściwości każdego wpisu, w tym słowniku jest obiektem, jednego z typów pochodnych typu <xref:System.Printing.IndexedProperties.PrintProperty>.  
  
3.  Wyliczanie elementów członkowskich w słowniku. Dla każdego z nich wykonaj następujące czynności.  
  
4.  Wartość każdego wpisu do rzutowania w górę <xref:System.Printing.IndexedProperties.PrintProperty> i użyć go do utworzenia <xref:System.Printing.IndexedProperties.PrintProperty> obiektu.  
  
5.  Pobierz typ <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> poszczególnych <xref:System.Printing.IndexedProperties.PrintProperty> obiektu.  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Printing.IndexedProperties.PrintProperty>
- <xref:System.Printing.PrintSystemObject>
- <xref:System.Printing.IndexedProperties>
- <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.PrintQueue>
- <xref:System.Collections.DictionaryEntry>
- [Dokumenty w WPF](documents-in-wpf.md)
- [Przegląd drukowania](printing-overview.md)
