---
title: Aplikacje klienckie warstwy środkowej
ms.date: 03/30/2017
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
ms.openlocfilehash: c50223a55765f211dae710f96bffa7716ce36b32
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598817"
---
# <a name="middle-tier-client-applications"></a>Aplikacje klienckie warstwy środkowej
W tym temacie omówiono różne problemy specyficzne dla aplikacji klienckich warstwy środkowej, które używają Windows Communication Foundation (WCF).  
  
## <a name="increasing-middle-tier-client-performance"></a>Zwiększenie wydajności klienta warstwy środkowej  
 W porównaniu z poprzednimi technologiami komunikacyjnymi, takimi jak usługi sieci Web przy użyciu ASP.NET, tworzenie wystąpienia klienta WCF może być bardziej skomplikowane ze względu na rozbudowany zestaw funkcji WCF. Na przykład po <xref:System.ServiceModel.ChannelFactory%601> otwarciu obiektu można ustanowić bezpieczną sesję z usługą, a także procedurę, która wydłuża czas uruchamiania dla wystąpienia klienta. Zazwyczaj te dodatkowe funkcje funkcji nie wpływają na aplikacje klienckie znacznie, ponieważ klient WCF wykonuje kilka wywołań, a następnie zamyka je.  
  
 Aplikacje klienckie warstwy środkowej mogą jednak szybko tworzyć wiele obiektów klienta programu WCF i w efekcie zwiększyć wymagania dotyczące inicjacji. Istnieją dwa główne podejścia do zwiększania wydajności aplikacji warstwy środkowej podczas wywoływania usług:  
  
- Buforuj obiekt klienta WCF i ponownie go wykorzystuje do kolejnych wywołań, tam gdzie to możliwe.  
  
- Utwórz <xref:System.ServiceModel.ChannelFactory%601> obiekt, a następnie użyj tego obiektu, aby utworzyć nowe obiekty kanału klienta WCF dla każdego wywołania.  
  
 Kwestie, które należy wziąć pod uwagę podczas korzystania z tych metod, obejmują:  
  
- Jeśli usługa utrzymuje stan specyficzny dla klienta przy użyciu sesji, nie można ponownie użyć klienta WCF warstwy środkowej z wieloma żądaniami warstwy klienta, ponieważ stan usługi jest powiązany z klientem warstwy środkowej.  
  
- Jeśli usługa musi przeprowadzić uwierzytelnianie dla poszczególnych klientów, należy utworzyć nowego klienta dla każdego żądania przychodzącego w warstwie środkowej zamiast ponownego używania klienta WCF warstwy środkowej (lub obiektu kanału klienta WCF), ponieważ nie można modyfikować poświadczeń klienta warstwy środkowej po utworzeniu klienta WCF (lub <xref:System.ServiceModel.ChannelFactory%601> ).  
  
- Kanały i klienci tworzone przez kanały są bezpieczne dla wątków, ale mogą nie obsługiwać jednoczesnego zapisywania więcej niż jednego komunikatu w sieci. W przypadku wysyłania dużych komunikatów, szczególnie w przypadku przesyłania strumieniowego, operacja wysyłania może blokować oczekiwanie na zakończenie innego procesu wysyłania. Powoduje to dwa rodzaje problemów: Brak współbieżności i możliwości zakleszczenia, jeśli przepływ sterowania powróci do usługi w sposób ponownie korzystający z kanału (to oznacza, że udostępniony klient wywołuje usługę, której ścieżka kodu powoduje wywołanie zwrotne do klienta udostępnionego). Jest to istotne niezależnie od typu używanego klienta programu WCF.  
  
- Należy obsługiwać błędne kanały, niezależnie od tego, czy dany kanał jest udostępniany. Gdy kanały są ponownie używane, kanał błędu może trwać więcej niż jedno oczekujące żądanie lub wysłać.  
  
 Aby zapoznać się z przykładem, w którym przedstawiono najlepsze rozwiązania dotyczące ponownego korzystania z klienta dla wielu żądań, zobacz [powiązanie danych w kliencie ASP.NET](../samples/data-binding-in-an-aspnet-client.md).  
  
 Ponadto można zwiększyć wydajność uruchamiania dla klientów korzystających z typów danych, które można serializować przy użyciu <xref:System.Xml.Serialization.XmlSerializer> generowania i kompilowania kodu serializacji dla tych typów danych w czasie wykonywania, co może spowodować spowolnienie wydajności. [Narzędzie do przesyłania metadanych modelu ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) może zwiększyć wydajność uruchamiania tych aplikacji, generując wymagany kod serializacji z skompilowanych zestawów dla aplikacji. Aby uzyskać więcej informacji, zobacz [How to: ulepszanie czasu uruchamiania aplikacji klienckich WCF przy użyciu elementu XmlSerializer](startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="see-also"></a>Zobacz też

- [Uzyskiwanie dostępu do usług za pomocą klienta WCF](accessing-services-using-a-client.md)
