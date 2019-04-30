---
title: Atrybuty modelu ServiceModel i odwołanie modelu ServiceDescription
ms.date: 03/30/2017
ms.assetid: 4ab86b17-eab9-4846-a881-0099f9a7cc64
ms.openlocfilehash: 022731d7d6e60d36c5f4a595edc90aaff0586a79
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747744"
---
# <a name="servicemodel-attributes-and-servicedescription-reference"></a>Atrybuty modelu ServiceModel i odwołanie modelu ServiceDescription
*Drzewa opis* jest hierarchia typów (począwszy od <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> klasy) ze sobą opisują każdego aspektu usługi. Windows Communication Foundation (WCF) używa drzewa opis do tworzenia środowiska uruchomieniowego prawidłową usługę, do publikowania w sieci Web Services Description Language (WSDL), język definicji schematu XML (XSD) i asercji zasad (metadanymi) o usługę, której klienci mogą używać do Nawiązywanie połączenia i korzystać z niej, a także o generowaniu różnych kodem i konfiguracją pliku reprezentujących wartości drzewa opis.  
  
 W tym temacie opisano sposób umowy związane z właściwości są uzyskiwane z kontraktu usługi oraz sposób ich zaimplementowane i dodane do drzewa opis. W niektórych przypadkach wartości atrybutów są konwertowane na właściwości zachowanie i zachowanie zostanie wstawiony na drzewie opis. Aby uzyskać więcej informacji na temat sposobu opis wartości drzewa są konwertowane na metadanych, zobacz [ServiceDescription odwołania i kodu WSDL](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md).  
  
## <a name="mapping-operations-to-the-description-tree"></a>Operacje mapowania do drzewa opis  
 W przypadku aplikacji WCF kontraktów usług są modelowane przy interfejsów (lub klasy), używanie atrybutów do oznaczania interfejs lub klasa i jej metod jako grupowanie operacji. Gdy <xref:System.ServiceModel.ServiceHost> klasa jest otwierana, uwzględnione przez i scalone z informacji o konfiguracji w drzewie opis implementacji i kontraktów usług.  
  
 Istnieją dwa typy modeli operacji: *parametru* modelu i *kontraktu komunikatu* modelu. Model parametr wykorzystuje zarządzanych metod, które nie mają parametrów lub typ zwracanej wartości, która jest oznaczona za <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType> klasy. W tym modelu deweloperów sterowania serializacją parametry i zwracane wartości, ale WCF generuje wartości, które są używane do wypełnienia drzewa opis dla usługi i zmiana kontraktu.  
  
 Określone w plikach konfiguracji powiązania są ładowane bezpośrednio do <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A?displayProperty=nameWithType> właściwości.  
  
|Właściwość ServiceBehaviorAttribute|Wartość drzewa opisu, których to dotyczy|  
|---------------------------------------|-------------------------------------|  
|Nazwa|<xref:System.ServiceModel.Description.ServiceDescription.Name%2A>|  
|Przestrzeń nazw|<xref:System.ServiceModel.Description.ServiceDescription.Namespace%2A>|  
|ConfigurationName|<xref:System.ServiceModel.Description.ServiceDescription.ConfigurationName%2A>|  
|IgnoreExtensionDataObject|Zestawy <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.IgnoreExtensionDataObject%2A> właściwości dla wszystkich operacji.|  
|MaxItemsInObjectGraph|Zestawy <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> właściwości dla wszystkich operacji.|  
  
|Właściwość atrybutu ServiceContractAttribute|Wartość drzewa opisu, których to dotyczy|  
|---------------------------------------|-------------------------------------|  
|CallbackContract|<xref:System.ServiceModel.Description.ContractDescription.CallbackContractType%2A>, <xref:System.ServiceModel.Description.MessageDescription> dodawane do wszystkich operacji <xref:System.ServiceModel.Description.OperationDescription.Messages%2A>.|  
|ConfigurationName|<xref:System.ServiceModel.Description.ContractDescription.ConfigurationName%2A>|  
|protectionLevel|<xref:System.ServiceModel.Description.ContractDescription.ProtectionLevel%2A> i prawdopodobnie poziomów ochrony podrzędnych. Aby uzyskać więcej informacji na temat hierarchii poziom ochrony, zobacz [zrozumieć poziom ochrony](../../../../docs/framework/wcf/understanding-protection-level.md).|  
|SessionMode|<xref:System.ServiceModel.Description.ContractDescription.SessionMode%2A>|  
  
|ServiceKnownTypesAttribute Value|Wartość drzewa opisu, których to dotyczy|  
|--------------------------------------|-------------------------------------|  
|MethodName|<xref:System.ServiceModel.Description.OperationDescription.KnownTypes%2A>|  
  
|Wartość OperationContractAttribute|Wartość drzewa opisu, których to dotyczy|  
|--------------------------------------|-------------------------------------|  
|Akcja|<xref:System.ServiceModel.Description.MessageDescription.Action%2A> Aby uzyskać komunikatu wyjściowego lub wejściowego wiadomości, w zależności od umowy/wywołania zwrotnego kontraktu.|  
|AsyncPattern|W przypadku opcji true <xref:System.ServiceModel.Description.OperationDescription.BeginMethod%2A> i <xref:System.ServiceModel.Description.OperationDescription.EndMethod%2A>|  
|IsOneWay|Mapy do pojedynczego <xref:System.ServiceModel.Description.MessageDescription> w <xref:System.ServiceModel.Description.OperationDescription.Messages%2A>|  
|IsInitiating|<xref:System.ServiceModel.Description.OperationDescription.IsInitiating%2A>|  
|IsTerminating|<xref:System.ServiceModel.Description.OperationDescription.IsTerminating%2A>|  
|Nazwa|<xref:System.ServiceModel.Description.OperationDescription.Name%2A>|  
|protectionLevel|<xref:System.ServiceModel.Description.OperationDescription.ProtectionLevel%2A> i prawdopodobnie poziomów ochrony podrzędnych. Aby uzyskać więcej informacji na temat hierarchii poziom ochrony, zobacz [zrozumieć poziom ochrony](../../../../docs/framework/wcf/understanding-protection-level.md).|  
|Parametr ReplyAction|<xref:System.ServiceModel.Description.MessageDescription.Action%2A> Aby uzyskać komunikatu wyjściowego lub wejściowego wiadomości, w zależności od umowy/wywołania zwrotnego kontraktu.|  
  
|Wartość FaultContractAttribute|Wartość drzewa opisu, których to dotyczy|  
|----------------------------------|-------------------------------------|  
|Akcja|<xref:System.ServiceModel.Description.FaultDescription.Action%2A> w zależności od umowy/wywołania zwrotnego kontraktu.|  
|DetailType|<xref:System.ServiceModel.Description.FaultDescription.DetailType%2A>|  
|Nazwa|<xref:System.ServiceModel.Description.FaultDescription.Name%2A>|  
|Przestrzeń nazw|<xref:System.ServiceModel.Description.FaultDescription.Namespace%2A>|  
|protectionLevel|<xref:System.ServiceModel.Description.FaultDescription.ProtectionLevel%2A>|  
  
|Obiekt DataContractFormatAttribute wartość|Wartość drzewa opisu, których to dotyczy|  
|---------------------------------------|-------------------------------------|  
|Zastosowanie|<xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> Wartość jest ustawiana na <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> dla tej operacji.|  
  
|Wartość XmlSerializerFormatAttribute|Wartość drzewa opisu, których to dotyczy|  
|----------------------------------------|-------------------------------------|  
|Styl|To <xref:System.ServiceModel.XmlSerializerFormatAttribute> właściwość jest ustawiona na <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> dla tej operacji.|  
|Zastosowanie|<xref:System.ServiceModel.XmlSerializerFormatAttribute> Jest ustawiona na <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> dla tej operacji.|  
  
|Wartość TransactionFlowAttribute|Wartość drzewa opisu, których to dotyczy|  
|------------------------------------|-------------------------------------|  
|TransactionFlowOption|<xref:System.ServiceModel.TransactionFlowAttribute> Jest dodawany jako zachowanie operacji <xref:System.ServiceModel.Description.OperationDescription.Behaviors%2A> właściwości.|  
  
|Wartość MessageContractAttribute|Wartość drzewa opisu, których to dotyczy|  
|------------------------------------|-------------------------------------|  
|protectionLevel|<xref:System.ServiceModel.Description.MessageDescription.ProtectionLevel%2A>|  
|WrapperName|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperName%2A>|  
|WrapperNamespace|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperNamespace%2A>|  
  
|Wartość w parametrze MessageHeaderAttribute|Wartość drzewa opisu, których to dotyczy|  
|----------------------------------|-------------------------------------|  
|aktora|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A> Aby uzyskać odpowiedni nagłówek w <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A> Aby uzyskać odpowiedni nagłówek w <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Nazwa|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> Aby uzyskać odpowiedni nagłówek w <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Przestrzeń nazw|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A> Aby uzyskać odpowiedni nagłówek w <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|protectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A> Aby uzyskać odpowiedni nagłówek w <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Przekaźnik|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A> Aby uzyskać odpowiedni nagłówek w <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
  
|Wartość atrybutu MessageBodyMemberAttribute|Wartość drzewa opisu, których to dotyczy|  
|--------------------------------------|-------------------------------------|  
|Nazwa|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> Aby uzyskać odpowiednie części w <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Przestrzeń nazw|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A> Aby uzyskać odpowiednie części w <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Zamówienie|<xref:System.ServiceModel.Description.MessagePartDescription.Index%2A> Aby uzyskać odpowiednie części w <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|protectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A> Aby uzyskać odpowiednie części w <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
|Wartość MessageHeaderArrayAttribute|Wartość drzewa opisu, których to dotyczy|  
|---------------------------------------|-------------------------------------|  
|aktora|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>|  
|Nazwa|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
|Przestrzeń nazw|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>|  
|protectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>|  
|Przekaźnik|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>|  
  
|Wartość MessagePropertyAttribute|Wartość drzewa opisu, których to dotyczy|  
|------------------------------------|-------------------------------------|  
|Nazwa|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
  
|Wartość MessageParameterAttribute|Wartość drzewa opisu, których to dotyczy|  
|-------------------------------------|-------------------------------------|  
|Nazwa|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> Aby uzyskać odpowiednie części w <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
 Aby uzyskać więcej informacji na temat sposobu opis wartości drzewa są konwertowane na metadanych, zobacz [ServiceDescription odwołania i kodu WSDL](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md).  
  
## <a name="see-also"></a>Zobacz także

- [Odwołania do elementu ServiceDescription i kodu WSDL](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)
