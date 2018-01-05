---
title: "Atrybuty modelu ServiceModel i odwołanie modelu ServiceDescription"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ab86b17-eab9-4846-a881-0099f9a7cc64
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61a0811176a5db17e040073d031fa50865a09857
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="servicemodel-attributes-and-servicedescription-reference"></a>Atrybuty modelu ServiceModel i odwołanie modelu ServiceDescription
*Drzewa opis* jest hierarchia typów (począwszy od <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> klasy) ze sobą opisują każdego aspektu działania usługi. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]używa opis drzewa do kompilacji do publikowania Web Services Description Language (WSDL), języka definicji schematu XML (XSD) i potwierdzeń zasad (metadanymi) o usługę, której klienci mogą używać do łączenia się i korzystać z usługi oraz moduł wykonawczy prawidłową usługę Generowanie różne reprezentacje kodem i konfiguracją pliku wartości drzewa opis.  
  
 W tym temacie opisano sposób kontraktu związane z właściwości są uzyskiwane z kontraktu usługi oraz sposób ich zaimplementowane i dodane do drzewa opis. W niektórych przypadkach wartości atrybutów są konwertowane na zachowanie właściwości i zachowanie zostanie wstawiony w drzewie opis. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Opis drzewa wartości są konwertowane na metadanych, zobacz [ServiceDescription i kodu WSDL odwołanie](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md).  
  
## <a name="mapping-operations-to-the-description-tree"></a>Operacje mapowania do drzewa opis  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji, kontraktów usług są modelowane przez interfejsy lub klasy wykorzystujące atrybuty można oznaczyć jako grupowanie operacji interfejsu lub klasy i metody. Gdy <xref:System.ServiceModel.ServiceHost> klasy jest otwarty, zostaną uwzględnione w i łączone z informacjami o konfiguracji w drzewie opis implementacji i kontrakty usług.  
  
 Istnieją dwa typy operacji modeli: *parametru* modelu i *kontraktu komunikatu* modelu. Model parametru używa metody zarządzanych, które ma parametr lub typ zwracanej wartości, która jest oznaczona przez <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType> klasy. W tym modelu deweloperów sterowania serializacją parametrów i wartości zwracane, ale [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje wartości, które są używane do wypełnienia drzewa opis dla usługi i jego kontraktu.  
  
 Określona w plikach konfiguracji powiązania są ładowane bezpośrednio do <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A?displayProperty=nameWithType> właściwości.  
  
|Właściwość atrybutu ServiceBehaviorAttribute|Wartość drzewa opisu, których to dotyczy|  
|---------------------------------------|-------------------------------------|  
|Nazwa|<xref:System.ServiceModel.Description.ServiceDescription.Name%2A>|  
|Przestrzeń nazw|<xref:System.ServiceModel.Description.ServiceDescription.Namespace%2A>|  
|ConfigurationName|<xref:System.ServiceModel.Description.ServiceDescription.ConfigurationName%2A>|  
|IgnoreExtensionDataObject|Ustawia <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.IgnoreExtensionDataObject%2A> właściwości dla wszystkich operacji.|  
|MaxItemsInObjectGraph|Ustawia <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> właściwości dla wszystkich operacji.|  
  
|Właściwość ServiceContractAttribute|Wartość drzewa opisu, których to dotyczy|  
|---------------------------------------|-------------------------------------|  
|CallbackContract|<xref:System.ServiceModel.Description.ContractDescription.CallbackContractType%2A>, <xref:System.ServiceModel.Description.MessageDescription> dodawane do wszystkich operacji <xref:System.ServiceModel.Description.OperationDescription.Messages%2A>.|  
|ConfigurationName|<xref:System.ServiceModel.Description.ContractDescription.ConfigurationName%2A>|  
|protectionLevel|<xref:System.ServiceModel.Description.ContractDescription.ProtectionLevel%2A>i prawdopodobnie poziomów ochrony podrzędnych. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Hierarchia poziomu ochrony, zobacz [poziom ochrony opis](../../../../docs/framework/wcf/understanding-protection-level.md).|  
|SessionMode|<xref:System.ServiceModel.Description.ContractDescription.SessionMode%2A>|  
  
|Wartość ServiceKnownTypesAttribute|Wartość drzewa opisu, których to dotyczy|  
|--------------------------------------|-------------------------------------|  
|MethodName|<xref:System.ServiceModel.Description.OperationDescription.KnownTypes%2A>|  
  
|Wartość OperationContractAttribute|Wartość drzewa opisu, których to dotyczy|  
|--------------------------------------|-------------------------------------|  
|Akcja|<xref:System.ServiceModel.Description.MessageDescription.Action%2A>dane wyjściowe komunikatu lub komunikatu wejściowego, w zależności od kontraktu/wywołanie zwrotne kontraktu.|  
|AsyncPattern|Jeśli PRAWDA, <xref:System.ServiceModel.Description.OperationDescription.BeginMethod%2A> i<xref:System.ServiceModel.Description.OperationDescription.EndMethod%2A>|  
|Ustawienie właściwości IsOneWay|Mapy do pojedynczego <xref:System.ServiceModel.Description.MessageDescription> w<xref:System.ServiceModel.Description.OperationDescription.Messages%2A>|  
|IsInitiating|<xref:System.ServiceModel.Description.OperationDescription.IsInitiating%2A>|  
|IsTerminating|<xref:System.ServiceModel.Description.OperationDescription.IsTerminating%2A>|  
|Nazwa|<xref:System.ServiceModel.Description.OperationDescription.Name%2A>|  
|protectionLevel|<xref:System.ServiceModel.Description.OperationDescription.ProtectionLevel%2A>i prawdopodobnie poziomów ochrony podrzędnych. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Hierarchia poziomu ochrony, zobacz [poziom ochrony opis](../../../../docs/framework/wcf/understanding-protection-level.md).|  
|Parametr ReplyAction|<xref:System.ServiceModel.Description.MessageDescription.Action%2A>dane wyjściowe komunikatu lub komunikatu wejściowego, w zależności od kontraktu/wywołanie zwrotne kontraktu.|  
  
|Wartość FaultContractAttribute|Wartość drzewa opisu, których to dotyczy|  
|----------------------------------|-------------------------------------|  
|Akcja|<xref:System.ServiceModel.Description.FaultDescription.Action%2A>w zależności od kontraktu/wywołanie zwrotne kontraktu.|  
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
|Właściwość TransactionFlowOption|<xref:System.ServiceModel.TransactionFlowAttribute> Jest dodawana jako zachowanie operacji do <xref:System.ServiceModel.Description.OperationDescription.Behaviors%2A> właściwości.|  
  
|Wartość MessageContractAttribute|Wartość drzewa opisu, których to dotyczy|  
|------------------------------------|-------------------------------------|  
|protectionLevel|<xref:System.ServiceModel.Description.MessageDescription.ProtectionLevel%2A>|  
|WrapperName|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperName%2A>|  
|WrapperNamespace|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperNamespace%2A>|  
  
|Wartość w parametrze MessageHeaderAttribute|Wartość drzewa opisu, których to dotyczy|  
|----------------------------------|-------------------------------------|  
|Aktora|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>odpowiednie nagłówka w<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Atrybut MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>odpowiednie nagłówka w<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Nazwa|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>odpowiednie nagłówka w<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Przestrzeń nazw|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>odpowiednie nagłówka w<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|protectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>odpowiednie nagłówka w<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Przekaźnik|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>odpowiednie nagłówka w<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
  
|Wartość atrybutu MessageBodyMemberAttribute|Wartość drzewa opisu, których to dotyczy|  
|--------------------------------------|-------------------------------------|  
|Nazwa|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>dla odpowiedniej części w<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Przestrzeń nazw|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>dla odpowiedniej części w<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Kolejność|<xref:System.ServiceModel.Description.MessagePartDescription.Index%2A>dla odpowiedniej części w<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|protectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>dla odpowiedniej części w<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
|Wartość MessageHeaderArrayAttribute|Wartość drzewa opisu, których to dotyczy|  
|---------------------------------------|-------------------------------------|  
|Aktora|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>|  
|Atrybut MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>|  
|Nazwa|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
|Przestrzeń nazw|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>|  
|protectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>|  
|Przekaźnik|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>|  
  
|Wartość MessagePropertyAttribute|Wartość drzewa opisu, których to dotyczy|  
|------------------------------------|-------------------------------------|  
|Nazwa|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
  
|Wartość MessageParameterAttribute|Wartość drzewa opisu, których to dotyczy|  
|-------------------------------------|-------------------------------------|  
|Nazwa|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>dla odpowiedniej części w<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Opis drzewa wartości są konwertowane na metadanych, zobacz [ServiceDescription i kodu WSDL odwołanie](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania do elementu ServiceDescription i kodu WSDL](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)
