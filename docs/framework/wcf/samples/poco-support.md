---
title: Obsługa obiektów POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: 86ade3a6b045f6f7c57e4a95936b4f1574b51ff0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334903"
---
# <a name="poco-support"></a>Obsługa obiektów POCO
Niniejszy przykład pokazuje obsługę serializacji typów nieoznaczone. oznacza to typów, do których nie zostały zastosowane atrybutów serializacji, czasami określane jako typy zwykłe stare CLR obiektu (— POCO). <xref:System.Runtime.Serialization.DataContractSerializer> Wnioskuje kontraktu danych dla wszystkich publicznych nieoznaczone typy, które mają domyślnego konstruktora. Kontrakty danych umożliwia przekazanie ze strukturą danych do i z usługi. Aby uzyskać więcej informacji na temat nieoznaczone typy zobacz [typów możliwych do serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), ale używa liczby zespolone zamiast pierwotnych typów liczbowych. Ponadto jest on podobny do [podstawowego kontraktu danych](../../../../docs/framework/wcf/samples/basic-data-contract.md) przykładowy, chyba że <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybuty nie są używane.  
  
 Usługa jest hostowana przez Internetowe usługi informacyjne (IIS), a klient to aplikacja konsoli (.exe).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 `ComplexNumber` Klasa jest używana w `ServiceContract`. `ComplexNumber` Typ nie ma <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybuty, jak pokazano w poniższym przykładowym kodzie. Domyślnie wszystkie właściwości publiczne i pola są serializowane.  
  
```csharp
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [Typy z możliwością serializowania](../../../../docs/framework/wcf/feature-details/serializable-types.md)
