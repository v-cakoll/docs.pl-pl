---
title: 'Instrukcje: Rejestrowanie i konfigurowanie monikera usługi'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: 2f8f19e70b3345b61f1f5caba2fc6f764b58cc9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54593800"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a>Instrukcje: Rejestrowanie i konfigurowanie monikera usługi
Przed użyciem monikera programu Windows Communication Foundation (WCF) w ramach aplikacji modelu COM z kontrolą typów kontraktu, musisz zarejestrować wymaganych typów opartego na atrybutach z modelem COM i konfigurowanie aplikacji modelu COM i moniker z powiązaniem wymagane Konfiguracja.  
  
### <a name="to-register-the-required-attributed-types-with-com"></a>Aby zarejestrować wymaganych typów opartego na atrybutach z modelem COM  
  
1.  Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia do pobierania metadanych kontraktu usługi WCF. Spowoduje to wygenerowanie kodu źródłowego dla zestawu klienta WCF i pliku konfiguracji aplikacji klienta.  
  
2.  Upewnij się, że typy w zestawie są oznaczone jako `ComVisible`. Aby to zrobić, Dodaj następujący atrybut w pliku AssemblyInfo.cs w projekcie programu Visual Studio.  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3.  Skompiluj zarządzanego klienta programu WCF jako zestawu o silnej nazwie. Ta migracja wymaga logowania przy użyciu pary kluczy kryptograficznych. Aby uzyskać więcej informacji, zobacz [podpisywanie zestawu za pomocą silnej nazwy](https://go.microsoft.com/fwlink/?LinkId=94874) w Podręczniku dewelopera programu .NET.  
  
4.  Narzędzie rejestracji zestawów (Regasm.exe), za pomocą `/tlb` opcję, aby można było zarejestrować typy w zestawie przy użyciu modelu COM.  
  
5.  Aby dodać zestaw do globalnej pamięci podręcznej, należy użyć narzędzia Globalna pamięć podręczna zestawów (Gacutil.exe).  
  
    > [!NOTE]
    >  Podpisywanie zestawu i dodanie go do globalnej pamięci podręcznej zestawów są opcjonalne kroki, ale upraszczają proces ładowania zestawu we właściwej lokalizacji, w czasie wykonywania.  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a>Aby skonfigurować aplikacji modelu COM i moniker przy użyciu konfiguracji powiązania wymagane  
  
-   Umieść definicji powiązania (generowany przez [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) w pliku konfiguracyjnym aplikacji wygenerowanego klienta) w pliku konfiguracyjnym aplikacji klienckiej. Na przykład Visual Basic 6.0 pliku wykonywalnego o nazwie CallCenterClient.exe, konfiguracji powinny być umieszczane w pliku o nazwie CallCenterConfig.exe.config w tym samym katalogu co plik wykonywalny. Aplikacja kliencka można teraz używać krótkiej nazwy. Pamiętaj, że konfiguracja powiązania nie jest wymagane, jeśli przy użyciu jednej ze standardowych powiązań typów dostarczonych przez architekturę WCF.  
  
     Następujący typ jest zarejestrowany.  
  
    ```  
    using System.ServiceModel;  
  
    ...  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     Aplikacja jest udostępniana przy użyciu `wsHttpBinding` powiązania. Dla danego typu i konfiguracji aplikacji są używane następujące ciągi moniker przykładu.  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     Można użyć dowolnego z tych ciągów krótkiej nazwy z aplikacji Visual Basic 6.0, po dodaniu odwołania do zestawu, który zawiera `IMathService` typów, jak pokazano w poniższym przykładowym kodzie.  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     W tym przykładzie definicji dla konfiguracji powiązania `Binding1` są przechowywane w pliku konfiguracji odpowiednio nazwanych w aplikacji klienckiej, takich jak vb6appname.exe.config.  
  
    > [!NOTE]
    >  Możesz użyć podobny kod w języku C#, C++ lub inna aplikacja języka .NET.  
  
    > [!NOTE]
    >  : Jeśli moniker jest źle sformułowany lub jeśli usługa jest niedostępna, wywołanie `GetObject` zwraca błąd "Nieprawidłowa składnia". Jeśli zostanie wyświetlony ten błąd, upewnij się, moniker elementu, którego używasz jest poprawna i ta usługa jest dostępna.  
  
     Chociaż ten temat koncentruje się na temat korzystania z kodu VB 6.0 monikera programu, można użyć krótkiej nazwy z innych języków. Gdy używanie monikera z C++ code Svcutil.exe generowane zestawu należy zaimportować za pomocą "no_namespace named_guids — raw_interfaces_only —", jak pokazano w poniższym kodzie.  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     Modyfikuje definicje interfejsu importowanych, tak, aby zwrócić wszystkie metody `HResult`. Zwracane wartości są konwertowane na parametrów out. Ogólny wykonywanie metody pozostaje taka sama. Dzięki temu można ustalić przyczynę Wystąpił wyjątek podczas wywoływania metody na serwerze proxy. Ta funkcja jest dostępna tylko w kodzie języka C++.  
  
## <a name="see-also"></a>Zobacz także
- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
