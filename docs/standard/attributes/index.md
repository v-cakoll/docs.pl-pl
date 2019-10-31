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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130903"
---
# <a name="extending-metadata-using-attributes"></a>Rozszerzanie metadanych za pomocą atrybutów
Środowisko uruchomieniowe języka wspólnego umożliwia dodawanie opisowych deklaracji słów kluczowych, takich jak atrybuty, do elementów programistycznych, takich jak typy, pola, metody i właściwości. Podczas kompilowania kodu środowiska uruchomieniowego jest on konwertowany do języka pośredniego firmy Microsoft (MSIL) i umieszczony wewnątrz przenośnego pliku wykonywalnego (PE) wraz z metadanymi generowanymi przez kompilator. Atrybuty umożliwiają umieszczanie w metadanych dodatkowych informacji opisowych, które można wyodrębnić przy użyciu usług odbicia środowiska uruchomieniowego. Kompilator tworzy atrybuty przy deklarowaniu wystąpień klas specjalnych, które pochodzą z <xref:System.Attribute?displayProperty=nameWithType>.  
  
 .NET Framework używa atrybutów z różnych powodów i rozwiązywania wielu problemów. Atrybuty opisują sposób serializacji danych, określają cechy, które są używane do wymuszania zabezpieczeń i ograniczają optymalizacje przez kompilator just-in-Time (JIT), dzięki czemu kod pozostaje łatwy do debugowania. Atrybuty mogą również rejestrować nazwę pliku lub autora kodu lub kontrolować widoczność formantów i członków podczas opracowywania formularzy.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Stosowanie atrybutów](../../../docs/standard/attributes/applying-attributes.md)|Opisuje sposób zastosowania atrybutu do elementu kodu.|  
|[Wpisywanie atrybutów niestandardowych](../../../docs/standard/attributes/writing-custom-attributes.md)|Opisuje sposób projektowania klas atrybutów niestandardowych.|  
|[Pobieranie informacji przechowywanych w atrybutach](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)|Opisuje sposób pobierania atrybutów niestandardowych dla kodu, który jest ładowany do kontekstu wykonywania.|  
|[Składniki samoopisujące się i metadane](../../../docs/standard/metadata-and-self-describing-components.md)|Zawiera omówienie metadanych i opis sposobu ich implementacji w .NET Framework przenośnym pliku wykonywalnym (PE).|  
|[Instrukcje: ładowanie zestawów do kontekstu Reflection-Only](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Wyjaśnia, jak pobrać informacje o atrybutach niestandardowych w kontekście tylko odbicia.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Attribute?displayProperty=nameWithType>
