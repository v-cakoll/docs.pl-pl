---
title: "Obsługa obiektów POCO"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0607ea270b32aa0ae02e6ed0b0eecfa6c4c0d054
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="poco-support"></a>Obsługa obiektów POCO
W tym przykładzie przedstawiono obsługę serializacji nieoznaczone typy; oznacza to, że typy, do których nie zostały zastosowane atrybutów serializacji, czasami określane jako typy zwykłego obiektu CLR stary (POCO). <xref:System.Runtime.Serialization.DataContractSerializer> Wnioskuje kontraktu danych dla wszystkich publicznych nieoznaczone typy, które ma domyślnego konstruktora. Kontrakty danych umożliwiają przekazywania strukturalnych danych do i z usług. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]nieoznaczone typy, zobacz [typów możliwych do serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), ale używa liczby złożone zamiast liczbowych typów pierwotnych. Jest również podobne do [podstawowego kontraktu danych](../../../../docs/framework/wcf/samples/basic-data-contract.md) przykładowe, z wyjątkiem <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybuty nie są używane.  
  
 Usługa jest obsługiwana przez Internet Information Services (IIS) i klient jest aplikacji konsoli (.exe).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 `ComplexNumber` Klasa jest używana w `ServiceContract`. `ComplexNumber` Typ nie ma <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów, jak pokazano w poniższym kodzie próbki. Domyślnie wszystkie właściwości publiczne i pola są serializowane.  
  
```  
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 [Typów możliwych do serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md)
