---
title: Rozszerzanie metadanych za pomocą atrybutów
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: b3a106eb58de4865e260a43c8466019e738510f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73130903"
---
# <a name="extending-metadata-using-attributes"></a>Rozszerzanie metadanych za pomocą atrybutów
Czas wykonywania języka wspólnego umożliwia dodawanie deklaracji opisowych przypominających słowa kluczowe, nazywanych atrybutami, aby dodawać adnotacje do elementów programowania, takich jak typy, pola, metody i właściwości. Podczas kompilowania kodu dla czasu wykonawczego, jest konwertowany na język pośredni firmy Microsoft (MSIL) i umieszczone wewnątrz przenośnego pliku wykonywalnego (PE) wraz z metadanych generowanych przez kompilator. Atrybuty umożliwiają umieszczanie dodatkowych informacji opisowych w metadanych, które można wyodrębnić przy użyciu usług odbicia czasu wykonywania. Kompilator tworzy atrybuty podczas deklarowania wystąpień <xref:System.Attribute?displayProperty=nameWithType>klas specjalnych, które pochodzą z .  
  
 Program .NET Framework używa atrybutów z różnych powodów i do rozwiązania wielu problemów. Atrybuty opisują sposób serializacji danych, określają cechy, które są używane do wymuszania zabezpieczeń i ograniczają optymalizacje przez kompilator just-in-time (JIT), dzięki czemu kod pozostaje łatwy do debugowania. Atrybuty można również rejestrować nazwę pliku lub autora kodu lub kontrolować widoczność formantów i elementów członkowskich podczas tworzenia formularzy.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Stosowanie atrybutów](../../../docs/standard/attributes/applying-attributes.md)|Opisuje sposób stosowania atrybutu do elementu kodu.|  
|[Wpisywanie atrybutów niestandardowych](../../../docs/standard/attributes/writing-custom-attributes.md)|Opisuje sposób projektowania klas atrybutów niestandardowych.|  
|[Pobieranie informacji przechowywanych w atrybutach](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)|W tym artykule opisano sposób pobierania atrybutów niestandardowych dla kodu, który jest ładowany do kontekstu wykonywania.|  
|[Składniki samoopisujące się i metadane](../../../docs/standard/metadata-and-self-describing-components.md)|Zawiera omówienie metadanych i opisuje, jak jest zaimplementowana w pliku przenośnego pliku wykonywalnego programu .NET Framework (PE).|  
|[Porady: ładowanie zestawów do kontekstu Reflection-Only](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|W tym artykule wyjaśniono, jak pobrać niestandardowe informacje o atrybutach w kontekście tylko do odbicia.|  
  
## <a name="reference"></a>Dokumentacja  
 <xref:System.Attribute?displayProperty=nameWithType>
