---
title: Aplikacje klienckie warstwy środkowej
ms.date: 03/30/2017
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
ms.openlocfilehash: 4cca832266b2eb2ab7b1b4eb1a5fe937525db97d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="middle-tier-client-applications"></a>Aplikacje klienckie warstwy środkowej
W tym temacie omówiono różne kwestie związane z aplikacje klienckie warstwy środkowej, które używają usług Windows Communication Foundation (WCF).  
  
## <a name="increasing-middle-tier-client-performance"></a>Zwiększanie wydajności klienckie warstwy środkowej  
 W porównaniu do poprzednich technologii komunikacji, takich jak usługi sieci Web przy użyciu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], utworzenie wystąpienia klienta WCF może być bardziej skomplikowane, gdyż zestaw zaawansowanych funkcji WCF. Na przykład, jeśli <xref:System.ServiceModel.ChannelFactory%601> otworzyć obiektu może nawiązać bezpiecznej sesji przy użyciu usługi, procedury, która zwiększa czas uruchamiania dla wystąpienia klienta. Zazwyczaj te możliwości dodatkowych funkcji nie wpływa na aplikacje klienckie znacznie od klienta WCF kilka wywołań, a następnie zamyka.  
  
 Aplikacje klienckie warstwy środkowej, jednak można szybko utworzyć wiele obiektów klienta WCF i, w związku z tym wystąpić inicjowania zwiększone wymagania. Istnieją dwa główne podejścia do zwiększenia wydajności warstwy środkowej aplikacji podczas wywoływania usługi:  
  
-   Buforowanie obiektu klienta WCF i użyć go ponownie dla kolejnych wywołań w miarę możliwości.  
  
-   Utwórz <xref:System.ServiceModel.ChannelFactory%601> obiekt, a następnie użyj obiektu do utworzenia nowego klienta WCF obiektów kanał dla każdego wywołania.  
  
 Zagadnienia do rozważenia przy użyciu tych metod obejmują:  
  
-   Jeśli usługa jest obsługę stanu specyficzne dla klienta przy użyciu sesji, następnie możesz ponownie użyć klienta WCF warstwy środkowej warstwy klienta wiele żądań, ponieważ stan usługi jest powiązany z klienckie warstwy środkowej.  
  
-   Jeśli usługa musi wykonać uwierzytelnianie na poszczególnych klientów, należy utworzyć nowego klienta dla każdego żądania przychodzącego na warstwy środkowej, zamiast ponownego użycia warstwy środkowej klienta WCF (lub obiekt kanału klienta WCF), ponieważ poświadczenia klienta warstwy środkowej Nie można zmodyfikować po klienta WCF (lub <xref:System.ServiceModel.ChannelFactory%601>) został utworzony.  
  
-   Kanałów i klientów utworzone przez kanały są bezpieczne wątkowo, ich może nie obsługiwać zapisywania więcej niż jeden komunikat można przewodowo jednocześnie. W przypadku wysyłania dużych wiadomości, zwłaszcza w wypadku przesyłania strumieniowego, operacji wysyłania mogą blokować oczekiwanie na inny Wyślij, aby zakończyć. Powoduje to, że dwa rodzaje problemów: Brak współbieżności i możliwość zakleszczenia, jeśli zwróci przepływu sterowania usługą ponowne użycie kanału (oznacza to, udostępnionych klient wywołuje usługi których wyniki ścieżki kodu w wywołaniu zwrotnym do udostępnionego klienta). Dotyczy to niezależnie od typu klienta WCF, których można użyć ponownie.  
  
-   Musi obsługiwać błędnej kanały niezależnie od tego, czy udział kanału. Gdy kanały są używane ponownie, jednak źle działający kanału można wyłączyć więcej niż jedno oczekujące żądanie lub wysyłania.  
  
 Na przykład, który pokazuje najlepsze rozwiązania dotyczące ponowne użycie klienta dla wielu żądań, zobacz [powiązania danych w kliencie programu ASP.NET](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md).  
  
 Ponadto można zwiększyć wydajność uruchamiania dla tych klientów, którzy używają typów danych, które są za pomocą serializacji <xref:System.Xml.Serialization.XmlSerializer> Generowanie i kompilacja kodu serializacji dla tych typów danych w czasie wykonywania, co może spowodować wolne uruchamiania wydajności. [Narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) może poprawić wydajność uruchamiania tych aplikacji przez generowania kodu serializacji niezbędne z skompilowane zestawy dla aplikacji. Aby uzyskać więcej informacji, zobacz [porady: poprawy uruchamiania czasu programu WCF aplikacje klienckie przy użyciu elementu XmlSerializer](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do usług za pomocą klienta WCF](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)
