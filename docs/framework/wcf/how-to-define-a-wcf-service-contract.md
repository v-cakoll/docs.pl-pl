---
title: "Instrukcje: Definiowanie kontraktu usługi Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service contracts [WCF], defining
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
caps.latest.revision: "58"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2ffe53d3e44f86feadc292eccb1692bd58a0c056
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a>Instrukcje: Definiowanie kontraktu usługi Windows Communication Foundation
Jest to pierwszy sześciu zadania wymagane do utworzenia podstawowego [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikacji. Omówienie sześciu wszystkich zadań, zobacz [Wprowadzenie — samouczek](../../../docs/framework/wcf/getting-started-tutorial.md) tematu.  
  
 Podczas tworzenia [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi, pierwszym zadaniem jest definiowanie kontraktu usługi. Kontrakt usługi określa, jakie operacje obsługuje usługi. Operację można traktować jako metoda usługi sieci Web. Kontrakty są tworzone przez definiowanie interfejsu C++, C# lub Visual Basic (VB). Każda metoda w interfejsie odpowiada określonej operacji usługi. Każdego interfejsu należy zastosować <xref:System.ServiceModel.ServiceContractAttribute> zastosować dla niego i każdej operacji musi być <xref:System.ServiceModel.OperationContractAttribute> atrybut zastosowany do niego. Jeśli metoda w interfejsie z atrybutem <xref:System.ServiceModel.ServiceContractAttribute> atrybut nie ma <xref:System.ServiceModel.OperationContractAttribute> atrybutu, że metoda nie jest uwidaczniana przez usługę.  
  
 Kod używany w tym zadaniu podano w przykładzie poniżej procedury.  
  
### <a name="to-define-a-service-contract"></a>Aby zdefiniować kontrakt usługi  
  
1.  Otwórz [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] jako administrator, klikając prawym przyciskiem myszy program w **Start** menu i wybierając **Uruchom jako administrator**.  
  
2.  Tworzenie projektu biblioteki usługi WCF, klikając **pliku** menu i wybierając **nowy**, **projektu**. W **nowy projekt** okna dialogowego, po lewej stronie okna dialogowego rozwiń **Visual C#** dla projektu C# lub **inne języki** , a następnie **Visual Basic** dla projektu Visual Basic. W obszarze Język wybrany wybierz **WCF** i listę szablonów projektu będzie wyświetlana na w górnej części okna dialogowego. Wybierz **biblioteki usługi WCF**i wpisz `GettingStartedLib` w **nazwa** pole tekstowe i `GettingStarted` w **Nazwa rozwiązania** textbox w dolnej części okna dialogowego.  
  
3.  Visual Studio utworzy projekt, który zawiera pliki 3: IService1.cs (lub IService1.vb) Service1.cs (lub Service1.vb) i pliku App.config.  Plik IService1 zawiera kontrakt usługi domyślne.  Plik Service1 zawiera domyślną implementację kontraktu usługi. Plik App.config zawiera konfiguracji potrzebne do załadowania domyślna usługa z hostem usługi WCF programu Visual Studio. Aby uzyskać więcej informacji o narzędziu Host usługi WCF, zobacz [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
4.  Otwórz plik IService1.cs lub IService1.vb i Usuń kod w deklaracji przestrzeni nazw, pozostawiając deklaracji przestrzeni nazw. W obszarze nazw deklaracji Zdefiniuj nowy interfejs o nazwie `ICalculator` jak pokazano w poniższym kodzie.  
  
    ```  
    // IService.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Runtime.Serialization;  
    using System.ServiceModel;  
    using System.Text;  
  
    namespace GettingStartedLib  
    {  
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
            public interface ICalculator  
            {  
                [OperationContract]  
                double Add(double n1, double n2);  
                [OperationContract]  
                double Subtract(double n1, double n2);  
                [OperationContract]  
                double Multiply(double n1, double n2);  
                [OperationContract]  
                double Divide(double n1, double n2);  
            }  
    }  
    ```  
  
    ```  
    ‘IService.vb  
    Imports System  
    Imports System.ServiceModel  
  
    Namespace GettingStartedLib  
  
        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _  
        Public Interface ICalculator  
  
            <OperationContract()> _  
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
        End Interface  
    End Namespace  
    ```  
  
     Ten kontrakt definiuje Kalkulator online. Powiadomienie `ICalculator` interfejs jest oznaczony atrybutem <xref:System.ServiceModel.ServiceContractAttribute> atrybutu. Ten atrybut definiuje przestrzeni nazw, która służy do odróżniania nazw kontraktu. Każda operacja Kalkulator jest oznaczony atrybutem <xref:System.ServiceModel.OperationContractAttribute> atrybutu.  
  
    > [!NOTE]
    >  Adnotuj interfejsu, elementu członkowskiego lub klasy za pomocą atrybutów, można usunąć część "Atrybutu" z nazwy atrybutu. Dlatego <xref:System.ServiceModel.ServiceContractAttribute> staje się `[ServiceContract]` w języku C# lub `<ServiceContract>` w języku Visual Basic.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Porady: Implementowanie kontraktu usługi](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [Wprowadzenie](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Host samodzielny](../../../docs/framework/wcf/samples/self-host.md)
