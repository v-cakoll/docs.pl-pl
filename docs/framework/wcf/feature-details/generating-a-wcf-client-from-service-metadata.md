---
title: Generowanie klienta programu WCF na podstawie metadanych usługi
ms.date: 03/30/2017
ms.assetid: 27f8f545-cc44-412a-b104-617e0781b803
ms.openlocfilehash: 938b1363be3b168fce74d80b47c9ae463d018669
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70892746"
---
# <a name="generating-a-wcf-client-from-service-metadata"></a>Generowanie klienta programu WCF na podstawie metadanych usługi
W tym temacie opisano, jak używać różnych przełączników w programie Svcutil. exe do generowania klientów z dokumentów metadanych.  
  
 Dokumenty metadanych mogą znajdować się w magazynie trwałym lub być pobierane w trybie online. Pobieranie online następuje przy użyciu protokołu WS-MetadataExchange lub protokołu Microsoft Discovery (DISCO). Svcutil. exe wystawia następujące żądania metadanych jednocześnie w celu pobrania metadanych:  
  
- Żądanie WS-MetadataExchange (MEX) do podanego adresu.  
  
- Żądanie MEX do podanego adresu `/mex` z dołączonym.  
  
- Żądanie DISCO (przy użyciu [DiscoveryClientProtocol](https://go.microsoft.com/fwlink/?LinkId=94777) z usług sieci Web ASP.NET) do podanego adresu.  
  
 Svcutil. exe generuje klienta na podstawie Web Services Description Language (WSDL) lub pliku zasad otrzymanego z usługi. Główna nazwa użytkownika (UPN) jest generowana przez połączenie nazwy użytkownika z "\@", a następnie dodanie w pełni kwalifikowanej nazwy domeny (FQDN). Jednak w przypadku użytkowników, którzy zarejestrowali się w Active Directory, ten format nie jest prawidłowy, a nazwa UPN wygenerowanego przez narzędzie powoduje błąd uwierzytelniania Kerberos z następującym komunikatem o błędzie: **Próba logowania nie powiodła się.** Aby rozwiązać ten problem, należy ręcznie naprawić plik klienta wygenerowany przez narzędzie.  
  
```console
svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>  
```  
  
## <a name="referencing-and-sharing-types"></a>Odwołania i typy udostępniania  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/Reference:\<ścieżka pliku >**|Odwołuje się do typów w określonym zestawie. Podczas generowania klientów należy użyć tej opcji, aby określić zestawy, które mogą zawierać typy reprezentujące importowane metadane.<br /><br /> Krótka forma:`/r`|  
|**/excludeType:\<wpisz >**|Określa w pełni kwalifikowaną lub kwalifikowaną dla zestawu nazwę typu, który ma zostać wykluczony z przywoływanych typów kontraktu.<br /><br /> Krótka forma:`/et`|  
  
## <a name="choosing-a-serializer"></a>Wybieranie serializatora  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/serializer:Auto**|Automatycznie wybiera serializator. Używa `DataContract` serializatora. Jeśli to się nie powiedzie, `XmlSerializer` jest używany.<br /><br /> Krótka forma:`/ser:Auto`|  
|**/serializer:DataContractSerializer**|Generuje typy danych używające `DataContract` serializatora do serializacji i deserializacji.<br /><br /> Krótka forma:`/ser:DataContractSerializer`|  
|**/serializer:XmlSerializer**|Generuje typy danych używające `XmlSerializer` do serializacji i deserializacji.<br /><br /> Krótka forma:`/ser:XmlSerializer`|  
|**/importXmlTypes**|Konfiguruje`DataContract` `IXmlSerializable` serializator do importowania typów, które nie są typami. `DataContract`<br /><br /> Krótka forma:`/ixt`|  
|**/dataContractOnly**|Generuje kod tylko `DataContract` dla typów. `ServiceContract`typy są generowane.<br /><br /> Należy określić tylko lokalne pliki metadanych dla tej opcji.<br /><br /> Krótka forma:`/dconly`|  
  
## <a name="choosing-a-language-for-the-client"></a>Wybieranie języka dla klienta  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/Language:\<język >**|Określa język programowania, który ma być używany do generowania kodu. Podaj nazwę języka zarejestrowana w pliku Machine. config lub w pełni kwalifikowaną nazwę klasy, która dziedziczy z <xref:System.CodeDom.Compiler.CodeDomProvider>.<br /><br /> Wartości: c#, CS, CSharp, VB, vbs, VisualBasic, VBScript, JavaScript, c++, MC, CPP<br /><br /> Wartość domyślna: CSharp<br /><br /> Krótka forma:`/l`<br /><br /> Aby uzyskać więcej informacji, zobacz [Klasa CodeDomProvider](https://go.microsoft.com/fwlink/?LinkId=94778).|  
  
## <a name="choosing-a-namespace-for-the-client"></a>Wybieranie przestrzeni nazw dla klienta  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/Namespace:\<ciąg, ciąg >**|Określa mapowanie ze schematu `targetNamespace` WSDL lub XML do przestrzeni nazw środowiska uruchomieniowego języka wspólnego (CLR). Używanie symbolu wieloznacznego (*) `targetNamespace` dla map `targetNamespaces` wszystkich bez jawnego mapowania do tej przestrzeni nazw środowiska CLR.<br /><br /> Aby upewnić się, że nazwa kontraktu komunikatu nie koliduje z nazwą operacji, należy zakwalifikować odwołanie do typu z podwójnymi średnikami`::`() lub upewnić się, że nazwy są unikatowe.<br /><br /> Wartooć Pochodny od docelowej przestrzeni nazw dokumentu schematu dla `DataContracts`. Domyślna przestrzeń nazw jest używana dla wszystkich innych typów wygenerowanych.<br /><br /> Krótka forma:`/n`|  
  
## <a name="choosing-a-data-binding"></a>Wybieranie powiązania danych  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/enableDataBinding**|Implementuje interfejs na wszystkich `DataContract` typach, aby włączyć powiązanie danych. <xref:System.ComponentModel.INotifyPropertyChanged><br /><br /> Krótka forma:`/edb`|  
  
## <a name="generating-configuration"></a>Generowanie konfiguracji  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/config:\<configFile>**|Określa nazwę pliku dla wygenerowanego pliku konfiguracji.<br /><br /> Domyślnie: output. config|  
|**/mergeConfig**|Scala wygenerowaną konfigurację w istniejący plik, zamiast zastąpić istniejący plik.|  
|**/noConfig**|Nie Generuj plików konfiguracyjnych.|  
  
## <a name="see-also"></a>Zobacz także

- [Używanie metadanych](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Przegląd architektury metadanych](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
