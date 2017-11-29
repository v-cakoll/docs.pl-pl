---
title: "Aplikacje klienckie warstwy środkowej"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 893fa027d2f1eb4fa3782b9119f6ae2d4a78d700
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="middle-tier-client-applications"></a>Aplikacje klienckie warstwy środkowej
W tym temacie omówiono różne kwestie związane z aplikacje klienckie warstwy środkowej, które używają [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="increasing-middle-tier-client-performance"></a>Zwiększanie wydajności klienckie warstwy środkowej  
 W porównaniu do poprzednich technologii komunikacji, takich jak usługi sieci Web przy użyciu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], tworzenie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wystąpienie klienta może być bardziej skomplikowane, gdyż zestaw zaawansowanych funkcji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Na przykład, jeśli <xref:System.ServiceModel.ChannelFactory%601> otworzyć obiektu może nawiązać bezpiecznej sesji przy użyciu usługi, procedury, która zwiększa czas uruchamiania dla wystąpienia klienta. Zazwyczaj te możliwości dodatkowych funkcji nie mają wpływu na aplikacje klienckie znacznie w porównaniu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klient wykonuje wiele wywołań, a następnie zamyka.  
  
 Aplikacje klienckie warstwy środkowej, jednak można utworzyć wiele [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiekty klienta szybko i w związku z tym wystąpić inicjowania zwiększone wymagania. Istnieją dwa główne podejścia do zwiększenia wydajności warstwy środkowej aplikacji podczas wywoływania usługi:  
  
-   Pamięć podręczna [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta obiektu i użyć go ponownie dla kolejnych wywołań w miarę możliwości.  
  
-   Utwórz <xref:System.ServiceModel.ChannelFactory%601> obiekt, a następnie użyj tego obiektu, aby utworzyć nowy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiekty kanału klienta dla każdego wywołania.  
  
 Zagadnienia do rozważenia przy użyciu tych metod obejmują:  
  
-   Jeśli usługa jest obsługę stanu specyficzne dla klienta przy użyciu sesji, a następnie nie można użyć ponownie warstwy środkowej [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta z warstwą klienta wielu żądań, ponieważ stan usługi jest powiązany z klienckie warstwy środkowej.  
  
-   Jeśli usługa musi wykonać uwierzytelnianie na poszczególnych klientów, należy utworzyć nowego klienta dla każdego żądania przychodzącego na warstwy środkowej, zamiast ponownego użycia warstwy środkowej [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta (lub [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiektu kanału klienta) ponieważ klienta poświadczenia warstwy środkowej nie można zmodyfikować po [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta (lub <xref:System.ServiceModel.ChannelFactory%601>) został utworzony.  
  
-   Kanałów i klientów utworzone przez kanały są bezpieczne wątkowo, ich może nie obsługiwać zapisywania więcej niż jeden komunikat można przewodowo jednocześnie. W przypadku wysyłania dużych wiadomości, zwłaszcza w wypadku przesyłania strumieniowego, operacji wysyłania mogą blokować oczekiwanie na inny Wyślij, aby zakończyć. Powoduje to, że dwa rodzaje problemów: Brak współbieżności i możliwość zakleszczenia, jeśli zwróci przepływu sterowania usługą ponowne użycie kanału (oznacza to, udostępnionych klient wywołuje usługi których wyniki ścieżki kodu w wywołaniu zwrotnym do udostępnionego klienta). Dotyczy to niezależnie od typu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta można użyć ponownie.  
  
-   Musi obsługiwać błędnej kanały niezależnie od tego, czy udział kanału. Gdy kanały są używane ponownie, jednak źle działający kanału można wyłączyć więcej niż jedno oczekujące żądanie lub wysyłania.  
  
 Na przykład, który pokazuje najlepsze rozwiązania dotyczące ponowne użycie klienta dla wielu żądań, zobacz [powiązania danych w kliencie programu ASP.NET](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md).  
  
 Ponadto można zwiększyć wydajność uruchamiania dla tych klientów, którzy używają typów danych, które są za pomocą serializacji <xref:System.Xml.Serialization.XmlSerializer> Generowanie i kompilacja kodu serializacji dla tych typów danych w czasie wykonywania, co może spowodować wolne uruchamiania wydajności. [Narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) może poprawić wydajność uruchamiania tych aplikacji przez generowania kodu serializacji niezbędne z skompilowane zestawy dla aplikacji. Aby uzyskać więcej informacji, zobacz [porady: poprawy uruchamiania czasu programu WCF aplikacje klienckie przy użyciu elementu XmlSerializer](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do usług za pomocą klienta WCF](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)
