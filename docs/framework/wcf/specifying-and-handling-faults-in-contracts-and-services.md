---
title: Określanie i obsługa błędów w kontraktach i usługach
ms.date: 03/30/2017
helpviewer_keywords:
- handling faults [WCF]
ms.assetid: a9696563-d404-4905-942d-1e0834c26dea
ms.openlocfilehash: 93ebbf3410dc197982ca617b4e989d07f0e0b454
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806503"
---
# <a name="specifying-and-handling-faults-in-contracts-and-services"></a>Określanie i obsługa błędów w kontraktach i usługach
Aplikacje systemu Windows Communication Foundation (WCF) obsługują wystąpienia błędu przez mapowanie wyjątków zarządzanych obiektów na obiekty błędu protokołu SOAP i błędów SOAP do obiektów zarządzanych wyjątkach. Tematy w tej sekcji omówiono sposób projektowania umów do udostępnienia błąd warunków jako niestandardowych błędach SOAP, jak zwrócić takie błędy jako część implementacji usługi i jak klienci catch takie błędy.  
  
## <a name="error-handling-overview"></a>Omówienie obsługi błędów  
 We wszystkich aplikacjach zarządzanych błędy przetwarzania są reprezentowane przez <xref:System.Exception> obiektów. W aplikacjach opartego na protokole SOAP, takich jak aplikacje WCF metody usługi komunikują się za pomocą protokołu SOAP komunikatów "fault" informacje o błędzie przetwarzania. Błędach SOAP są typy wiadomości, które są zawarte w metadanych dla operacji usługi i dlatego utworzyć kontrakt błędu, której klienci mogą używać, aby ich operacja bardziej niezawodne lub interaktywnego. Ponadto ponieważ błędach SOAP są wyrażane klientom w postaci XML, jest to system wysokiej interoperacyjne typu, używany przez klientów na dowolnej platformie SOAP można zwiększyć zasięg aplikacji WCF.  
  
 Ponieważ aplikacje WCF uruchomione oba rodzaje systemów błąd, wszystkie informacje o zarządzanym wyjątku wysyłana do klienta należy przekonwertować z wyjątków w błędach SOAP w usłudze, wysyłane i przekonwertować z błędach SOAP wyjątki błędów w klientach WCF. W przypadku klientów dupleksu zamówień klienta można również wysłać błędach SOAP do usługi. W obu przypadkach można użyć domyślnego zachowania wyjątek usługi lub jawnie można kontrolować, czy — i w jaki sposób — wyjątki są mapowane na komunikaty o błędach.  
  
 Dwa typy o błędach SOAP mogą być wysyłane: *zadeklarowany* i *niezadeklarowany*. Zadeklarowany w błędach SOAP są te, w których ma operacji <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> atrybut, który określa typ niestandardowy błędu protokołu SOAP. *Niezadeklarowany* błędach SOAP nie są określone w umowie dla operacji.  
  
 Zdecydowanie zaleca się, że operacje usługi deklarowanie ich usterek za pomocą <xref:System.ServiceModel.FaultContractAttribute> atrybutu formalnie określić wszystkie błędach SOAP, które klient może oczekiwać w trakcie normalnego przebiegu operacji. Zalecane jest także zwracany w przypadku błędu protokołu SOAP tylko te informacje, które klient musi wiedzieć, aby zminimalizować ujawnienie informacji.  
  
 Zazwyczaj usług (i klientów dupleks) wykonaj następujące kroki pomyślnie integracja obsługi błędów w swoich aplikacjach:  
  
-   Mapowanie stanów wyjątek do niestandardowych błędach SOAP.  
  
-   Klienci i usługi wysyłania i odbierania błędach SOAP jako wyjątki.  
  
 Ponadto klienci WCF i usługi można użyć błędach soap niezadeklarowany na potrzeby debugowania i można rozszerzyć domyślne zachowanie błędu. W poniższych sekcjach omówiono te zadania i pojęcia.  
  
## <a name="map-exceptions-to-soap-faults"></a>Mapowanie wyjątków do błędach SOAP  
 Pierwszym krokiem tworzenia obsługującego błędy operacji jest podjęcie pod jakimi warunkami aplikacja kliencka powinna informowany o błędach. Niektóre operacje mają błędy specyficzne dla ich funkcje. Na przykład `PurchaseOrder` operacji może zwrócić określone informacje do klientów, którzy nie mogą inicjować zamówienia zakupu. W pozostałych przypadkach takich jak `Calculator` usługi bardziej ogólnym `MathFault` błędu protokołu SOAP mogą mieć możliwość opisano wszystkie błędy w całej usługi. Po zidentyfikowaniu warunków błędów klientów usługi można utworzyć niestandardowego błędu protokołu SOAP i operacji może być oznaczony jako zwracanie tego błędu protokołu SOAP, gdy wystąpi jego odpowiedniego warunku błędu.  
  
 Aby uzyskać więcej informacji dotyczących tego kroku powstania usługi lub klienta, zobacz [definiowanie i określanie usterek](../../../docs/framework/wcf/defining-and-specifying-faults.md).  
  
## <a name="clients-and-services-handle-soap-faults-as-exceptions"></a>Klienci i usługi obsługi błędów SOAP jako wyjątki  
 Identyfikacji operacji błędów, definiowania niestandardowych błędach SOAP i oznaczenie te operacje jako zwracanie te błędy są pierwsze kroki w pomyślnym obsługi błędów w aplikacji WCF. Następnym krokiem jest prawidłowo zaimplementować wysyłania i odbierania tych błędów. Zwykle usług wysłać błędy poinformowanie aplikacji klienckich o warunkach błędów, ale dupleksu klientów można również wysłać błędach SOAP usług.  
  
 Aby uzyskać więcej informacji, zobacz [wysyłanie i odbieranie błędów](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="undeclared-soap-faults-and-debugging"></a>Niezadeklarowany SOAP błędów i debugowanie  
 Zadeklarowane błędach SOAP są bardzo przydatne w przypadku tworzenia niezawodne, współpraca, rozproszonych aplikacji. Jednak w niektórych przypadkach jest przydatne w przypadku usługi (lub dupleks klienta) do wysyłania niezadeklarowany błędu protokołu SOAP, który nie jest wymieniony w sieci Web Services Description Language (WSDL) dla tej operacji. Na przykład podczas tworzenia usługi, nieoczekiwany sytuacjach może wystąpić, w których jest przydatne w przypadku debugowania do wysyłania informacji do klienta. Ponadto można ustawić <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> właściwości lub <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> właściwości `true` aby umożliwić klientom uzyskanie informacji na temat wyjątki operacji wewnętrznych usług WCF. Zarówno wysyłania poszczególnych błędów i ustawienie właściwości zachowanie debugowania są opisane w [wysyłanie i odbieranie błędów](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
> [!IMPORTANT]
>  Ponieważ zarządzane wyjątki może ujawnić informacje o wewnętrznych aplikacji, ustawianie <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> do `true` może zezwolić klientom uzyskanie informacji o wyjątkach operacji wewnętrzny usługi, w tym osobiście WCF do zidentyfikowania lub inne poufne informacje.  
>   
>  W związku z tym ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> do `true` jest zalecana tylko sposób tymczasowo debugowania aplikacji usługi. Ponadto WSDL dla metody, która zwraca nieobsługiwanych wyjątków w ten sposób zarządzanych nie zawiera kontraktu dla <xref:System.ServiceModel.FaultException%601> typu <xref:System.ServiceModel.ExceptionDetail>. Klienci muszą oczekują możliwości nieznany błąd protokołu SOAP (zwracanych do klientów WCF jako <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> obiektów) można uzyskać informacji o debugowaniu poprawnie.  
  
## <a name="customizing-error-handling-with-ierrorhandler"></a>Dostosowywanie obsługi z interfejsy IErrorHandler błędów  
 Jeśli masz specjalne wymagania dotyczące dostosować komunikat odpowiedzi do klienta, w przypadku wyjątku poziomu aplikacji lub wykonać niektóre przetwarzania niestandardowego, po zwróceniu komunikat odpowiedzi, wdrożenie <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> interfejsu.  
  
## <a name="fault-serialization-issues"></a>Błąd serializacji problemów  
 Podczas deserializacji kontrakt błędu, WCF najpierw próbuje dopasować nazwę kontraktu błędu w wiadomości SOAP błędów typu kontraktu. Nie można znaleźć dokładnego dopasowania, następnie wyszukiwania na liście dostępnych błędów umów w kolejności alfabetycznej dla zgodne z typem. Jeśli odporność na dwa kontrakty są niezgodne typy (jest podklasą klasy inny, na przykład) niewłaściwego typu może służyć do zdeserializować błędu. To tylko wtedy, gdy kontrakt błędu nie określa nazwy, przestrzeń nazw i akcji. Aby zapobiec wystąpieniu tego problemu, należy zawsze pełnej kwalifikacji kontrakty błędów, określając nazwę przestrzeni nazw i atrybutów akcji. Ponadto jeśli zdefiniowano liczbę usterek powiązanych umów pochodzi z klasy podstawowej z udostępnionym, upewnij się, że Oznacz wszystkie nowe elementy członkowskie z `[DataMember(IsRequired=true)]`. Aby uzyskać więcej informacji na ten `IsRequired` , zobacz atrybut <xref:System.Runtime.Serialization.DataMemberAttribute>. Spowoduje to uniemożliwić klasę podstawową zgodne z typem i wymusić awarii, która może zostać przeprowadzona deserializacja poprawnego typu pochodnego.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.FaultException>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.FaultException>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 <xref:System.ServiceModel.XmlSerializerFormatAttribute>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.CommunicationException>  
 <xref:System.ServiceModel.FaultContractAttribute.Action%2A>  
 <xref:System.ServiceModel.FaultException.Code%2A>  
 <xref:System.ServiceModel.FaultException.Reason%2A>  
 <xref:System.ServiceModel.FaultCode.SubCode%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>  
 [Definiowanie i określanie błędów](../../../docs/framework/wcf/defining-and-specifying-faults.md)
