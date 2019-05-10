---
title: Określanie i obsługa błędów w kontraktach i usługach
ms.date: 03/30/2017
helpviewer_keywords:
- handling faults [WCF]
ms.assetid: a9696563-d404-4905-942d-1e0834c26dea
ms.openlocfilehash: b9d6a4e2bb6b7e5c750ff7dad92934c4337c0083
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64605947"
---
# <a name="specifying-and-handling-faults-in-contracts-and-services"></a>Określanie i obsługa błędów w kontraktach i usługach
Aplikacje Windows Communication Foundation (WCF) obsługują sytuacje przez mapowanie wyjątków zarządzanych obiektów na obiekty błędu protokołu SOAP i błędów protokołu SOAP do obiektów zarządzanych wyjątkach. Tematy w tej sekcji omówiono sposób projektowania umów do udostępnienia błąd warunków jako niestandardowych błędach SOAP, sposób zwracania tych błędów w ramach implementacji usługi i jak klienci wychwycić takie błędy.  
  
## <a name="error-handling-overview"></a>Omówienie obsługi błędów  
 We wszystkich aplikacjach zarządzanych błędy przetwarzania są reprezentowane przez <xref:System.Exception> obiektów. W aplikacjach opartego na protokole SOAP, takich jak aplikacje usługi WCF metody usługi komunikują się przy użyciu protokołu SOAP wiadomości błędu informacje o błędzie przetwarzania. Błędy protokołu SOAP są typy komunikatów, które są zawarte w metadanych dla operacji usługowej i z tego względu utworzyć kontrakt błędu, w której klienci mogą używać się ich działania, bardziej niezawodne lub interaktywnego. Ponadto ponieważ błędach SOAP są wyrażone klientom w postaci XML, to system wysokiej interoperacyjne typu, który klientów na dowolnej platformie protokołu SOAP, można użyć, zwiększa zasięg aplikacji WCF.  
  
 Ponieważ WCF aplikacje uruchamiane w ramach obu rodzajów błędów systemów, informacje o zarządzanym wyjątku, który jest wysyłany do klienta należy przekonwertować z wyjątków w błędach SOAP w usłudze, wysyłane i błędach SOAP konwertowane na wyjątki błędów w klientach programu WCF. W przypadku klientów dwukierunkowego zamówień klienta można także wysyłać błędach SOAP do usługi. W obu przypadkach można użyć zachowania wyjątek usługi domyślne lub jawnie można kontrolować, czy — i w jaki sposób — wyjątki są mapowane na komunikaty o błędach.  
  
 Dwa typy o błędach SOAP mogą być wysyłane: *zadeklarowana* i *niezadeklarowany*. Zadeklarowane w błędach SOAP są te, w których jest operacją <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> atrybut, który określa typ niestandardowy błędu protokołu SOAP. *Niezadeklarowany* błędach SOAP nie są określone w umowie dla danej operacji.  
  
 Zdecydowanie zaleca się, że operacje usług deklarowanie ich błędów przy użyciu <xref:System.ServiceModel.FaultContractAttribute> atrybutu, aby określić formalnie wszystkich błędach SOAP, które klient może oczekiwać w trakcie normalnego przebiegu operacji. Zalecane jest również zwrócić w błąd protokołu SOAP tylko te informacje, które klient musi wiedzieć, aby zminimalizować ujawnienie informacji.  
  
 Zazwyczaj usługi (i klientom dupleks) wykonaj następujące kroki, aby pomyślnie integracja obsługi błędów w swoich aplikacjach:  
  
- Warunków wyjątków są mapowane na niestandardowych błędach SOAP.  
  
- Klienci i usługi wysyłania i odbierania błędach SOAP jako wyjątki.  
  
 Ponadto WCF klientów i usług służy błędach soap niezadeklarowany na potrzeby debugowania i rozszerzać domyślne zachowanie błąd. W poniższych sekcjach omówiono te zadania i pojęć.  
  
## <a name="map-exceptions-to-soap-faults"></a>Mapowanie wyjątki na błędy protokołu SOAP  
 Pierwszym krokiem w tworzeniu operacji, która obsługuje warunki błędów jest podjęcie decyzji, pod jakimi warunkami aplikacja kliencka powinien zostać poinformowany o błędach. Niektóre operacje mają błędy specyficzne dla ich funkcje. Na przykład `PurchaseOrder` operacji może zwrócić szczegółowe informacje dla klientów, którzy nie są już dozwolone do zainicjowania zamówienia zakupu. W innych przypadkach takich jak `Calculator` usługi bardziej ogólnej `MathFault` błąd protokołu SOAP może istnieć możliwość opisano wszystkie błędy w całej usługi. Po zidentyfikowaniu warunków błędów klientów usługi można skonstruować niestandardowy błąd protokołu SOAP i operacji może być oznaczona jako zwracanie ten błąd protokołu SOAP, gdy pojawia się jego odpowiadającego warunku błędu.  
  
 Aby uzyskać więcej informacji dotyczących tego kroku tworzenia Twojej usługi lub klienta, zobacz [definiowanie i określanie błędów](../../../docs/framework/wcf/defining-and-specifying-faults.md).  
  
## <a name="clients-and-services-handle-soap-faults-as-exceptions"></a>Klienci i usługi obsługi błędów protokołu SOAP, jako wyjątki  
 Identyfikowanie warunki błędów operacji, definiowanie niestandardowych błędach SOAP i oznaczanie tych operacji powrotu tych błędów należą pomyślnej obsługi błędów w aplikacji WCF pierwszych kroków. Następnym krokiem jest prawidłowo zaimplementować wysyłania i odbierania te błędy. Zazwyczaj usług wysłać błędy do informowania aplikacje klienckie o warunkach błędów, ale dwukierunkowego klientów można również wysłać błędach SOAP usługi.  
  
 Aby uzyskać więcej informacji, zobacz [wysyłanie i odbieranie błędów](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="undeclared-soap-faults-and-debugging"></a>Błędach SOAP niezadeklarowany i debugowania  
 Zadeklarowane błędach SOAP są bardzo przydatne w przypadku tworzenia niezawodnych, międzyoperacyjnych, rozproszonych aplikacji. Jednak w niektórych przypadkach jest przydatne w przypadku usługi (lub dupleks klienta) do wysyłania niezadeklarowany błąd protokołu SOAP, który nie jest wymieniony w sieci Web Services Description Language (WSDL) dla tej operacji. Na przykład podczas tworzenia usługi, nieoczekiwanych sytuacji może wystąpić, w których jest przydatne w przypadku debugowania do wysyłania informacji do klienta. Ponadto można ustawić <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> właściwości lub <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> właściwość `true` pozwalające klientom WCF uzyskanie informacji o wyjątkach operację usługi wewnętrznej. Wysyłanie poszczególnych błędów i ustawienie właściwości debugowania zachowania, które są opisane w [wysyłanie i odbieranie błędów](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
> [!IMPORTANT]
>  Ponieważ zarządzane wyjątki mogą ujawniać informacje o wewnętrznych aplikacji, ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> do `true` może pozwolić na WCF klientom uzyskanie informacji o wyjątkach operację usługi wewnętrznej, w tym osobiście danych osobowych lub inne poufne informacje.  
>   
>  W związku z tym, ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> do `true` jest zalecana tylko sposobem tymczasowo debugowania aplikacji usługi. Ponadto pliku WSDL dla zarządzanych przy użyciu metody, która zwraca nieobsługiwanych wyjątków w ten sposób nie zawiera kontrakt dla <xref:System.ServiceModel.FaultException%601> typu <xref:System.ServiceModel.ExceptionDetail>. Klienci muszą oczekują możliwości nieznany błąd protokołu SOAP (zwracane do klientów programu WCF jako <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> obiektów) Aby uzyskać informacje o debugowaniu prawidłowo.  
  
## <a name="customizing-error-handling-with-ierrorhandler"></a>Dostosowywanie obsługi za pomocą IErrorHandler błędów  
 Jeśli masz specjalne wymagania dostosować komunikat odpowiedzi do klienta w sytuacji wyjątku dodatku poziomu aplikacji lub wykonać niektóre niestandardowe przetwarzanie w po zwróceniu komunikat odpowiedzi, implementować <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> interfejsu.  
  
## <a name="fault-serialization-issues"></a>Problemy z serializacją błędów  
 Podczas deserializacji kontrakt błędu, WCF najpierw próbuje dopasować nazwę kontraktu błędu w wiadomości protokołu SOAP z typem umowy błędów. Nie można znaleźć dokładne dopasowanie, które następnie wyszuka listę błędów dostępnych umów w kolejności alfabetycznej na zgodne z typem. Jeśli dwa błędów kontrakty są niezgodne typy (jest podklasą innego, na przykład) niewłaściwy typ może służyć do deserializować błędu. To tylko wtedy, gdy kontrakt błędu nie określa nazwy, nazw i akcji. Aby zapobiec występowaniu tego problemu, zawsze w pełni kwalifikuje się błędów kontrakty, określając nazwę przestrzeni nazw i atrybutów akcji. Ponadto jeśli zdefiniowano liczbę usterek powiązanych umów pochodzi od udostępnionego klasy bazowej, upewnij się, że oznaczyć żadnych nowych elementów członkowskich z `[DataMember(IsRequired=true)]`. Aby uzyskać więcej informacji na ten `IsRequired` , zobacz atrybut <xref:System.Runtime.Serialization.DataMemberAttribute>. Spowoduje to uniemożliwić klasy bazowej na zgodny typ. i wymusić błędów, które ma zostać przeprowadzona do poprawnego typu pochodnego.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.FaultException>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.FaultException>
- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.CommunicationException>
- <xref:System.ServiceModel.FaultContractAttribute.Action%2A>
- <xref:System.ServiceModel.FaultException.Code%2A>
- <xref:System.ServiceModel.FaultException.Reason%2A>
- <xref:System.ServiceModel.FaultCode.SubCode%2A>
- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- [Definiowanie i określanie błędów](../../../docs/framework/wcf/defining-and-specifying-faults.md)
