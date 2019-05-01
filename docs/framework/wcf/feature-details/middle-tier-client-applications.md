---
title: Aplikacje klienckie warstwy środkowej
ms.date: 03/30/2017
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
ms.openlocfilehash: 667cc98f46b131fe91e17f3b1b16af429dc597ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948151"
---
# <a name="middle-tier-client-applications"></a>Aplikacje klienckie warstwy środkowej
W tym temacie omówiono różne problemy specyficzne dla aplikacje klienckie warstwy środkowej, które używają usług Windows Communication Foundation (WCF).  
  
## <a name="increasing-middle-tier-client-performance"></a>Zwiększanie wydajności klienckie warstwy środkowej  
 W porównaniu do poprzednich technologii komunikacji, takich jak usługi sieci Web przy użyciu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], utworzenie wystąpienia klienta WCF, mogą być bardziej złożone z powodu rozbudowanego zestawu funkcji programu WCF. Na przykład, gdy <xref:System.ServiceModel.ChannelFactory%601> otworzyć obiektu jego ustanowienia bezpiecznej sesji przy użyciu usługi, procedury, która zwiększa się czas uruchamiania dla wystąpienia klienta. Zazwyczaj te możliwości dodatkowych funkcji nie wpływają na aplikacje klienckie znacznie od klienta platformy WCF wykonuje kilka wywołań, a następnie zamyka.  
  
 Aplikacje klienckie warstwy środkowej, jednak można szybko utworzyć wiele obiektów klienta WCF i, co w efekcie środowiska inicjowania zwiększone wymagania. Istnieją dwa główne sposoby zwiększenie wydajności aplikacji warstwy środkowej podczas wywoływania usługi:  
  
- Buforowanie obiektu klienta programu WCF i użyć go ponownie dla kolejnych wywołań gdzie to możliwe.  
  
- Utwórz <xref:System.ServiceModel.ChannelFactory%601> obiektu, a następnie użyć tego obiektu, do tworzenia nowego klienta WCF obiektów kanał dla każdego wywołania.  
  
 Kwestie do rozważenia, korzystając z tych metod obejmują:  
  
- Jeśli usługa jest stanie specyficzne dla klienta przy użyciu sesji, następnie możesz ponownie użyć klienta WCF warstwy środkowej za pomocą żądań wielu klientów, ponieważ stan usługi jest powiązany z klienckie warstwy środkowej.  
  
- Jeśli usługa musi przeprowadzić uwierzytelnianie poszczególnych klientów, należy utworzyć nowego klienta dla każdego żądania przychodzącego w warstwie środkowej zamiast ponownego użycia warstwy środkowej klienta WCF (lub obiekt kanału klienta WCF), ponieważ poświadczenia klienta warstwy środkowej Nie można zmodyfikować po klienta WCF (lub <xref:System.ServiceModel.ChannelFactory%601>) został utworzony.  
  
- Kanałów i klientów utworzonych przez kanały jest metodą o bezpiecznych wątkach, może nie obsługują zapisywania jednocześnie więcej niż jeden komunikat podczas transmisji. W przypadku wysyłania dużych komunikatów, szczególnie w przypadku przesyłania strumieniowego, operacji wysyłania mogą blokować oczekiwanie na inny wysłać do ukończenia. Powoduje to, że dwa różne rodzaje problemów: Brak współbieżności i możliwość zakleszczenia przepływ sterowania wraca do usługi, o których ponowne użycie kanału (oznacza to, udostępnionych klienta wywołania usługi którego wyniki ścieżka kodu w wywołanie zwrotne do udostępnionego klienta). Ta zasada obowiązuje niezależnie od typu klienta WCF, których można użyć ponownie.  
  
- Musi obsługiwać uszkodzoną kanały, niezależnie od tego, czy udostępnianie kanału. Gdy kanały są używane ponownie, jednak błędną kanału można walce z więcej niż jedną oczekującego żądania lub wysyłania.  
  
 Aby uzyskać przykład demonstrujący najlepsze rozwiązania dotyczące ponowne użycie klienta dla wielu żądań, zobacz [powiązanie danych w kliencie programu ASP.NET](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md).  
  
 Ponadto, możesz zwiększyć wydajność uruchamiania dla tych klientów, którzy używają typów danych, które są możliwe do serializacji przy użyciu <xref:System.Xml.Serialization.XmlSerializer> Generowanie i kompilowanie kodu serializacji dla tych typów danych w czasie wykonywania, co może skutkować wydajności uruchamiania powolne. [Narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) może poprawić wydajność uruchamiania tych aplikacji, generowania kodu serializacji niezbędne z skompilowanych zestawów dla aplikacji. Aby uzyskać więcej informacji, zobacz [jak: Poprawę czasu uruchamiania programu WCF klienta aplikacji przy użyciu elementu XmlSerializer](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do usług za pomocą klienta WCF](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)
