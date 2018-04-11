---
title: Rozszerzanie metadanych za pomocą atrybutów
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata, extending
- attributes [.NET Framework], metadata
- elements [.NET Framework], attributes
- common language runtime, attributes
- annotating programming elements
- keyword-like descriptive declarations
- runtime, attributes
- extending metadata
ms.assetid: 30386922-1e00-4602-9ebf-526b271a8b87
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ae399e5213c95b29736c54fcc48ac45a778ba25b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="extending-metadata-using-attributes"></a>Rozszerzanie metadanych za pomocą atrybutów
Środowisko uruchomieniowe języka wspólnego pozwala dodać deklaracje opisowe typu słowo kluczowe, nazywany atrybuty dla adnotacji programowania elementów, takich jak typy, pola, metody i właściwości. Podczas kompilowania kodu środowiska uruchomieniowego jest konwertowane na język pośredni firmy Microsoft (MSIL) i umieszczony wewnątrz pliku wykonywalnego (PE) pliku przenośnego wraz z metadanych generowanych przez kompilator. Atrybuty pozwala na umieszczenie bardzo opisowe informacje do metadanych, który można wyodrębnić przy użyciu usługi czasu wykonywania odbicia. Kompilator tworzy atrybuty przy deklarowaniu wystąpienia klas specjalne, które pochodzą z <xref:System.Attribute?displayProperty=nameWithType>.  
  
 .NET Framework używa atrybutów z różnych powodów i rozwiązywać problemy dotyczące. Atrybuty opisują sposób serializacji danych, określ właściwości, które są używane do wymuszania zabezpieczeń i ograniczyć optymalizacje kompilatora just in time (JIT), kod jest łatwy do debugowania. Atrybuty można również zarejestrować nazwę pliku lub autorem kodu lub kontrolować widoczność formantów i elementów członkowskich podczas tworzenia formularzy.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Stosowanie atrybutów](../../../docs/standard/attributes/applying-attributes.md)|Opisuje sposób zastosować atrybut do elementu kodu.|  
|[Wpisywanie atrybutów niestandardowych](../../../docs/standard/attributes/writing-custom-attributes.md)|Opisuje sposób projektowania klas atrybutów niestandardowych.|  
|[Pobieranie informacji przechowywanych w atrybutach](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)|Opisuje sposób pobrać atrybutów niestandardowych dla kodu, który jest ładowany do kontekstu wykonywania.|  
|[Składniki samoopisujące się i metadane](../../../docs/standard/metadata-and-self-describing-components.md)|Zawiera omówienie metadanych oraz opisano, jak jest zaimplementowana w .NET Framework przenośnego (PE) pliku wykonywalnym.|  
|[Instrukcje: ładowanie zestawów do kontekstu Reflection-Only](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Wyjaśniono, jak można pobrać informacji o atrybutu niestandardowego w kontekstu reflection-only.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Attribute?displayProperty=nameWithType>
