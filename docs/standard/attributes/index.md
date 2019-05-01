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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a31082604048e71ebc7581b36857a8bfbd333c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969796"
---
# <a name="extending-metadata-using-attributes"></a>Rozszerzanie metadanych za pomocą atrybutów
Środowisko uruchomieniowe języka wspólnego pozwala na dodawanie deklaracje opisowe typu słowo kluczowe, o nazwie atrybutów, dodawać adnotacje do elementów programowania, takich jak typy, pola, metody i właściwości. Podczas kompilowania kodu dla środowiska uruchomieniowego jest konwertowany na składnię języka Microsoft intermediate language (MSIL) i umieszczone wewnątrz przenośny plik wykonywalny (PE) wraz z metadanymi generowanych przez kompilator. Atrybuty zezwala na umieszczenie bardzo opisowe informacje do metadanych, które można wyodrębnić za pomocą usług odbicia środowiska uruchomieniowego. Kompilator tworzy atrybutów w deklaracji wystąpienia klasy specjalne, które wynikają z <xref:System.Attribute?displayProperty=nameWithType>.  
  
 .NET Framework używa atrybutów z różnych powodów i rozwiązać wiele problemów. Atrybuty zawierają instrukcje dotyczące serializacji danych, określ cechy, które są używane do wymuszania zabezpieczeń i ograniczyć optymalizacji przez kompilator just-in-time (JIT), więc kod pozostaje ułatwia debugowanie. Atrybuty można również zarejestrować nazwę pliku i autor kodu lub kontrolowanie widoczności kontrolek i elementów członkowskich podczas projektowania formularzy.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Stosowanie atrybutów](../../../docs/standard/attributes/applying-attributes.md)|W tym artykule opisano sposób zastosowania atrybutu do elementu kodu.|  
|[Wpisywanie atrybutów niestandardowych](../../../docs/standard/attributes/writing-custom-attributes.md)|Opisuje sposób projektowania klas atrybutów niestandardowych.|  
|[Pobieranie informacji przechowywanych w atrybutach](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)|W tym artykule opisano sposób pobierania atrybutów niestandardowych dla kodu, który jest ładowany do kontekstu wykonywania.|  
|[Składniki samoopisujące się i metadane](../../../docs/standard/metadata-and-self-describing-components.md)|Zawiera omówienie metadanych, a w tym artykule opisano, jak jest zaimplementowane w .NET Framework przenośny plik wykonywalny (PE).|  
|[Instrukcje: Ładowanie zestawów do kontekstu Reflection-Only](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Wyjaśnia, jak można pobrać atrybutów niestandardowych informacji w kontekstu reflection-only.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Attribute?displayProperty=nameWithType>
