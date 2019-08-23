---
title: <webMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: a1d776730053cd6af3c930a33e13582a8906c4d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940398"
---
# <a name="webmessageencoding"></a>\<webMessageEncoding>
Umożliwia kodowanie komunikatów XML, JavaScript Object Notation (JSON) i "nieprzetworzony" zawartość binarną, która ma zostać odczytana i zapisywana w przypadku użycia w powiązaniu Windows Communication Foundation (WCF).  
  
 \<system.serviceModel>  
\<> powiązań  
\<customBinding>  
\<> powiązania  
\<webMessageEncoding>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<webMessageEncoding maxReadPoolSize="Integer"
                    maxWritePoolSize="Integer"
                    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`maxReadPoolSize`|Liczba wiadomości, które można jednocześnie odczytać bez przydziału nowych czytników. Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym. Wartość domyślna to 64 czytników dla każdego kodera wewnętrznego (text, JSON i "RAW").<br /><br /> Zwiększenie tej liczby powoduje zwiększenie zużycia pamięci, ale przygotowuje koder do rozpatruje nagłe rozerwanie komunikatów przychodzących, ponieważ może używać czytelników z puli, która została już utworzona, zamiast tworzyć nowe.|  
|`maxWritePoolSize`|Ilość komunikatów, które można jednocześnie wysłać bez przydziału nowych modułów zapisujących. Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym. Wartość domyślna to 16 modułów zapisujących dla każdego kodera wewnętrznego (text, JSON i "RAW").<br /><br /> Zwiększenie tej liczby powoduje zwiększenie zużycia pamięci, ale przygotowuje koder do rozpatruje nagłe rozerwanie komunikatów wychodzących, ponieważ może korzystać z autorów z puli, która została już utworzona, zamiast tworzyć nowe.|  
|`writeEncoding`|Określa kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu. Prawidłowe wartości to:<br /><br /> - UnicodeFffeTextEncoding: Kodowanie Unicode big endian.<br />- Utf16TextEncoding: Kodowanie Unicode.<br />-   Utf8TextEncoding: kodowanie 8-bitowe.<br /><br /> Wartość domyślna to Utf8TextEncoding. Ten atrybut jest typu <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> powiązania](../../../misc/binding.md)|Definiuje wszystkie możliwości powiązań niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Kodowanie jest procesem przekształcania komunikatu w sekwencję bajtów. Dekodowanie jest procesem wycofywania. Procesy te wymagają specyfikacji kodowania znaków.  
  
 `webMessageEncoding` Element działa przez delegowanie do serii koderów wewnętrznych w celu obsługi kodowania XML i JSON oraz "RAW" danych binarnych. To delegowanie odbywa się za pomocą złożonego kodera komunikatów.  
  
 Ten element powiązania i jego koder złożony są używane do sterowania kodowaniem w scenariuszach, które nie korzystają z `webHttpBinding` komunikatów SOAP używanych przez element. Te scenariusze obejmują "zwykłe stare XML" (POX), przenoszenie stanu reprezentacji (REST), Really Simple Syndication (RSS) i Atom Syndication oraz asynchroniczne skrypty JavaScript i XML (AJAX). Koder komunikatu złożonego nie obsługuje protokołu SOAP ani WS-Addressing.  
  
 Element Binding można skonfigurować przy użyciu kodowania znaków zapisu za pomocą `writeEncoding` atrybutu. Podana <xref:System.Text.Encoding> wartość określa zachowanie przy zapisie dla przypadków JSON i tekstowych XML. W przypadku odczytu wszystkie prawidłowe kodowanie komunikatów i kodowanie tekstu są zrozumiałe.  
  
 `maxReadPoolSize`i `maxWritePoolSize` można również użyć, aby ustawić maksymalną liczbę czytelników i autorów, które mają być odpowiednio przydzieloną. Domyślnie przydzielono 64 czytników i 16 składników zapisywania.  
  
 Domyślne ograniczenia dotyczące złożoności są również ustawiane za pomocą [ \<elementu readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) , aby chronić przed atakami klasy typu "odmowa usługi" (DOS), które próbują użyć złożoności komunikatów do powiązania zasobów przetwarzania punktów końcowych.  
  
## <a name="example"></a>Przykład  
  
```xml  
<webMessageEncoding maxReadPoolSize="256"
                    maxWritePoolSize="128"
                    messageVersion="None"
                    textEncoding="utf-8" />
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [Kodowanie komunikatu](message-encoding.md)
- [Wybieranie kodera komunikatów](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
