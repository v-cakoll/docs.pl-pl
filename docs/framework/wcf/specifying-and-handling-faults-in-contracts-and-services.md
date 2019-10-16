---
title: Określanie i obsługa błędów w kontraktach i usługach
ms.date: 03/30/2017
helpviewer_keywords:
- handling faults [WCF]
ms.assetid: a9696563-d404-4905-942d-1e0834c26dea
ms.openlocfilehash: bbc1ca97c8887ebdfbe30f7dd76549572367efbe
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321110"
---
# <a name="specifying-and-handling-faults-in-contracts-and-services"></a>Określanie i obsługa błędów w kontraktach i usługach

Aplikacje Windows Communication Foundation (WCF) obsługują sytuacje błędów, mapując zarządzane obiekty wyjątków do obiektów błędów SOAP i obiektów błędów SOAP na obiekty wyjątków zarządzanych. W tematach w tej sekcji omówiono sposób projektowania kontraktów w celu ujawnienia warunków błędów jako niestandardowych błędów SOAP, sposobu zwracania takich błędów w ramach implementacji usługi i sposobu, w jaki klienci przechwytują takie błędy.

## <a name="error-handling-overview"></a>Omówienie obsługi błędów

W przypadku wszystkich aplikacji zarządzanych błędy przetwarzania są reprezentowane przez obiekty <xref:System.Exception>. W aplikacjach opartych na protokole SOAP, takich jak aplikacje WCF, metody obsługi komunikują informacje o błędach przy użyciu komunikatów błędów protokołu SOAP. Błędy protokołu SOAP to typy komunikatów, które są uwzględnione w metadanych dla operacji usługi, dlatego należy utworzyć kontrakt błędów, za pomocą którego klienci mogą wykonywać działania bardziej niezawodne lub interaktywne. Ponadto, ponieważ błędy protokołu SOAP są wyrażane dla klientów w formularzu XML, jest to wysoce interoperacyjny system typów, który może być używany przez klientów na dowolnej platformie SOAP, zwiększając zasięg aplikacji WCF.

Ponieważ aplikacje WCF działają w obu typach systemów błędów, wszelkie zarządzane informacje o wyjątkach, które są wysyłane do klienta programu, muszą być konwertowane z wyjątków na błędy protokołu SOAP w usłudze, wysyłane i konwertowane z błędów SOAP na wyjątki błędów w klientach WCF. W przypadku klientów z dupleksem umowy klienckie mogą również wysyłać błędy SOAP z powrotem do usługi. W obu przypadkach można użyć domyślnych zachowań wyjątku usługi lub można jawnie kontrolować, czy i w jaki sposób wyjątki są mapowane na komunikaty o błędach.

Można wysyłać dwa typy błędów SOAP: *zadeklarowany* i *niezadeklarowany*. Zadeklarowane błędy protokołu SOAP to te, w których operacja ma atrybut <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>, który określa niestandardowy typ błędu SOAP. *Niezadeklarowany* Błędy SOAP nie są określone w kontrakcie dla operacji.

Zdecydowanie zaleca się, aby operacje usługi deklarują swoje błędy przy użyciu atrybutu <xref:System.ServiceModel.FaultContractAttribute> do formalnego określenia wszystkich błędów SOAP, które klient może otrzymać w normalnym przebiegu operacji. Zaleca się również zwrócenie informacji o błędach SOAP tylko wtedy, gdy klient musi wiedzieć, aby zminimalizować ujawnienie informacji.

Zazwyczaj usługi (i klient dupleksu) wykonaj następujące kroki, aby pomyślnie zintegrować obsługę błędów w swoich aplikacjach:

- Mapowanie warunków wyjątków na niestandardowe błędy SOAP.

- Klienci i usługi wysyłają i odbierają błędy protokołu SOAP jako wyjątki.

Ponadto klienci i usługi WCF mogą używać niezadeklarowanych błędów protokołu SOAP do celów debugowania i można zwiększyć domyślne zachowanie błędu. W poniższych sekcjach omówiono te zadania i koncepcje.

## <a name="map-exceptions-to-soap-faults"></a>Mapowanie wyjątków do błędów SOAP

Pierwszym krokiem w tworzeniu operacji, która obsługuje warunki błędów, jest określenie, w jaki sposób mają być informowane aplikacje klienckie o błędach. Niektóre operacje mają warunki błędów specyficzne dla ich funkcjonalności. Na przykład operacja `PurchaseOrder` może zwrócić określone informacje klientom, którzy nie będą już mogli inicjować zamówienia zakupu. W innych przypadkach, takich jak usługa `Calculator`, bardziej ogólny błąd protokołu SOAP `MathFault` może być w stanie opisać wszystkie warunki błędów w całej usłudze. Po zidentyfikowaniu warunków błędu klientów usługi można utworzyć niestandardowy błąd protokołu SOAP, a operacja może być oznaczona jako zwracająca ten błąd protokołu SOAP, gdy występuje odpowiedni warunek błędu.

Aby uzyskać więcej informacji na temat tworzenia usługi lub klienta, zobacz [Definiowanie i określanie błędów](defining-and-specifying-faults.md).

## <a name="clients-and-services-handle-soap-faults-as-exceptions"></a>Klienci i usługi obsługują błędy protokołu SOAP jako wyjątki

Identyfikowanie warunków błędów operacji, Definiowanie niestandardowych błędów protokołu SOAP i oznaczanie tych operacji jako zwracających te błędy to pierwsze kroki w przypadku pomyślnej obsługi błędów w aplikacjach WCF. Następnym krokiem jest poprawne zaimplementowanie wysyłania i otrzymywania tych błędów. Zazwyczaj usługi wysyłają błędy, aby informować aplikacje klienckie o błędach, ale klienci dupleksowi mogą również wysyłać błędy SOAP do usług.

Aby uzyskać więcej informacji, zobacz [wysyłanie i otrzymywanie błędów](sending-and-receiving-faults.md).

## <a name="undeclared-soap-faults-and-debugging"></a>Niezadeklarowane błędy i debugowanie protokołu SOAP

Zadeklarowane błędy protokołu SOAP są niezwykle przydatne do tworzenia niezawodnych, międzyoperacyjnych aplikacji rozproszonych. Jednak w niektórych przypadkach jest to przydatne w przypadku wysyłania niezadeklarowanych błędów SOAP przez usługę (lub klienta dupleksowego), która nie jest wymieniona w Web Services Description Language (WSDL) dla tej operacji. Na przykład podczas tworzenia usługi mogą wystąpić nieoczekiwane sytuacje, w których są przydatne do debugowania w celu wysyłania informacji z powrotem do klienta. Ponadto można ustawić właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> lub właściwość <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> na `true`, aby zezwolić klientom WCF na uzyskanie informacji o wyjątkach operacji wewnętrznej usługi. Zarówno wysyłanie pojedynczych błędów, jak i Ustawianie właściwości zachowania debugowania są opisane w temacie [wysyłanie i otrzymywanie błędów](sending-and-receiving-faults.md).

> [!IMPORTANT]
> Ponieważ zarządzane wyjątki mogą uwidaczniać wewnętrzne informacje o aplikacji, ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> na `true` może pozwolić klientom WCF uzyskać informacje o wyjątkach operacji usługi wewnętrznej, w tym identyfikowalnych przez użytkownika lub innych poufnych zawartych.
>
> W związku z tym ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> do `true` jest zalecane tylko jako sposób tymczasowego debugowania aplikacji usługi. Ponadto WSDL dla metody, która zwraca Nieobsłużone wyjątki zarządzane w ten sposób, nie zawiera kontraktu dla <xref:System.ServiceModel.FaultException%601> typu <xref:System.ServiceModel.ExceptionDetail>. Klienci muszą oczekiwać wystąpienia nieznanego błędu protokołu SOAP (zwracanego do klientów WCF jako obiektów <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>) w celu poprawnego uzyskania informacji o debugowaniu.

## <a name="customizing-error-handling-with-ierrorhandler"></a>Dostosowywanie obsługi błędów za pomocą IErrorHandler

Jeśli użytkownik ma specjalne wymagania, można dostosować komunikat odpowiedzi do klienta, gdy występuje wyjątek poziomu aplikacji lub wykonać niestandardowe przetwarzanie po zwróceniu komunikatu odpowiedzi, zaimplementować interfejs <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType>.

## <a name="fault-serialization-issues"></a>Problemy serializacji błędów

Podczas deserializacji kontraktu dotyczącego błędu usługa WCF najpierw próbuje dopasować nazwę kontraktu błędów w komunikacie protokołu SOAP z typem kontraktu błędu. Jeśli nie można znaleźć dokładnego dopasowania, przeszukasz listę dostępnych kontraktów błędów w kolejności alfabetycznej dla zgodnego typu. Jeśli dwa kontrakty błędów są zgodne z typami (jeden jest podklasą innego, na przykład) niewłaściwy typ może zostać użyty do deserializacji błędu. Ta sytuacja występuje tylko wtedy, gdy kontrakt błędu nie określa nazwy, przestrzeni nazw i akcji. Aby zapobiec wystąpieniu tego problemu, zawsze w pełni Zakwalifikuj kontrakty do błędów, określając nazwę, przestrzeń nazw i atrybuty akcji. Ponadto jeśli zdefiniowano wiele powiązanych umów o błędach pochodzących z udostępnionej klasy bazowej, upewnij się, że wszystkie nowe elementy członkowskie są oznaczone `[DataMember(IsRequired=true)]`. Aby uzyskać więcej informacji na temat tego atrybutu `IsRequired`, zobacz <xref:System.Runtime.Serialization.DataMemberAttribute>. Uniemożliwi to, aby Klasa bazowa była zgodna z typem zgodnym i wymusić deserializacja błędu do poprawnego typu pochodnego.

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
- [Definiowanie i określanie błędów](defining-and-specifying-faults.md)
