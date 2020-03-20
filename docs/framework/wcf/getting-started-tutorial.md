---
title: 'Samouczek: Wprowadzenie do aplikacji Windows Communication Foundation'
description: Te samouczki zawiera wprowadzenie do tworzenia aplikacji WCF.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: df73f953372202796cebce9d3e3f28bd617c67ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184124"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a>Samouczek: Wprowadzenie do aplikacji Windows Communication Foundation
Poniższa seria samouczków przedstawia środowisko programowania Programu Windows Communication Foundation (WCF). Praca za pomocą tych samouczków w kolejności daje wstępne zrozumienie kroków wymaganych do tworzenia aplikacji WCF. Po zakończeniu będziesz mieć uruchomionej usługi WCF i klienta WCF, który wywołuje usługę.

W samouczku przyjęto założenie, że używasz programu Visual Studio jako środowiska programistycznego. Jeśli używasz innego środowiska programistycznego, zignoruj instrukcje specyficzne dla programu Visual Studio.

Aby uzyskać przykładowe aplikacje WCF, które można pobrać i uruchomić, zobacz [przykłady Programu Windows Communication Foundation](samples/index.md). Aby zapoznać się z wprowadzeniem do próbek, zobacz [Wprowadzenie próbki](samples/getting-started-sample.md).

Aby uzyskać bardziej szczegółowe informacje na temat tworzenia usług i klientów, zobacz [Podstawowe programowanie WCF](basic-wcf-programming.md).

## <a name="wcf-tutorials"></a>Samouczki WCF

Pierwsze trzy samouczki opisują sposób definiowania umowy serwisowej WCF, jak ją zaimplementować i jak go hostować. Utworzona usługa jest hostowana samodzielnie w aplikacji konsoli. Usługi można również hostować w ramach internetowych usług informacyjnych firmy Microsoft (IIS). Aby uzyskać więcej informacji, zobacz [Jak: Hostować usługę WCF w usługach IIS](feature-details/how-to-host-a-wcf-service-in-iis.md). Chociaż kod służy do konfigurowania usługi w samouczku, można również [skonfigurować usługi w pliku konfiguracyjnym](configuring-services-using-configuration-files.md).

- [Samouczek: Definiowanie umowy serwisowej](how-to-define-a-wcf-service-contract.md)

    Tworzenie umowy WCF z interfejsem zdefiniowanym przez użytkownika. Ten kontrakt definiuje funkcje, które usługa udostępnia.

- [Samouczek: Zaimplementowanie umowy serwisowej](how-to-implement-a-wcf-contract.md)

    Po zdefiniowaniu umowy należy zaimplementować ją z klasą usługi.

- [Samouczek: Host i uruchom podstawową usługę](how-to-host-and-run-a-basic-wcf-service.md)

    Skonfiguruj punkt końcowy dla usługi i hostuj usługę w aplikacji konsoli. Aby usługa stała się aktywna, należy ją skonfigurować i hostować w środowisku wykonywania. To środowisko wykonywania tworzy usługę i kontroluje jej kontekst i okres istnienia.

Następne dwa samouczki opisują sposób tworzenia, konfigurowania i używania aplikacji klienckiej do wywoływania operacji udostępnianych przez usługę. Usługi publikują metadane definiujące informacje, które aplikacja kliencka musi komunikować się z usługą. Visual Studio automatyzuje proces uzyskiwania dostępu do tych metadanych i używa go do konstruowania aplikacji klienckiej dla usługi. Jeśli zdecydujesz się nie używać programu Visual Studio, możesz użyć [narzędzia Narzędzia metadanych ServiceModel (*Svcutil.exe).*](servicemodel-metadata-utility-tool-svcutil-exe.md)

- [Samouczek: Tworzenie klienta](how-to-create-a-wcf-client.md)

    Pobieranie metadanych do tworzenia serwera proxy klienta WCF z usługi WCF. Pobierasz metadane za pomocą programu Visual Studio, aby dodać odwołanie do usługi lub można użyć narzędzia Narzędzia Metadata ServiceModel. Należy określić punkt końcowy, który klient używa do uzyskania dostępu do usługi.

- [Samouczek: Korzystanie z klienta](how-to-use-a-wcf-client.md)

    Użyj serwera proxy klienta WCF do wywołania operacji usługi.

## <a name="reference"></a>Dokumentacja

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a>Zobacz też

- [Omówienie pojęć](conceptual-overview.md)
- [Przewodnik po dokumentacji](guide-to-the-documentation.md)
- [Co to jest Fundacja Komunikacji systemu Windows](whats-wcf.md)
- [Szczegóły funkcji WCF](feature-details/index.md)
- [Podstawowy cykl programowania](basic-programming-lifecycle.md)
- [Budowanie klientów](building-clients.md)
- [Podstawowe programowanie WCF](basic-wcf-programming.md)
- [Jak: Tworzenie kontraktu dupleksowego](feature-details/how-to-create-a-duplex-contract.md)
- [Jak: Dostęp do usług z umową dupleksową](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Narzędzie narzędzia Metadata Usługi ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Jak: Pobieranie dokumentów metadanych za pomocą programu Svcutil.exe](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [Jak: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracyjnego](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Używanie powiązań do konfigurowania usług i klientów](using-bindings-to-configure-services-and-clients.md)
- [Wprowadzenie próbki](samples/getting-started-sample.md)
- [Przykłady programu Windows Communication Foundation](samples/index.md)
- [Host samodzielny](samples/self-host.md)
