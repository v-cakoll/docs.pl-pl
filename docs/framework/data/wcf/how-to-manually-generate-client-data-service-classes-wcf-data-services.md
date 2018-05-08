---
title: 'Porady: ręczne Generowanie klasy usługi danych klienta (usługi danych WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: 24d19f10e025b765cfc7df73ba80d223fbfa8074
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a>Porady: ręczne Generowanie klasy usługi danych klienta (usługi danych WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] integruje się z programem Visual Studio umożliwiają automatyczne generowanie klasy usługi danych klienta, gdy używasz **Dodaj odwołanie do usługi** okno dialogowe, aby dodać odwołania do usługi danych w projekcie programu Visual Studio. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie odwołania do danych usługi](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md). Możesz też ręcznie wygenerować tej samej klasy usługi danych klienta przy użyciu narzędzia do generowania kodu, `DataSvcUtil.exe`. To narzędzie, który jest dołączony do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], generuje klasy .NET Framework z definicji usługi danych. Można go również używane do generowania klasy usługi danych z pliku modelu koncepcyjnego (CSDL), a także od pliku edmx, który reprezentuje model narzędzia Entity Framework w projektu programu Visual Studio.  
  
 W tym temacie tworzona klas usług danych klienta oparte na usługę Northwind przykładowych danych. Ta usługa jest utworzone po zakończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Przykłady w tym temacie wymagają pliku modelu koncepcyjnego dla modelu Northwind. Aby uzyskać więcej informacji, zobacz [porady: EdmGen.exe używany do generowania modelu i mapowania plików](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md). Przykłady w tym temacie wymagają pliku edmx modelu Northwind. Aby uzyskać więcej informacji, zobacz [pliku Przegląd edmx](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4).  
  
### <a name="to-generate-c-classes-that-support-data-binding"></a>Można wygenerować klas C#, które obsługuje powiązanie danych  
  
-   W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  Należy zastąpić wartość dostarczona do `/uri:` parametru o identyfikatorze URI wystąpienia usługi Northwind przykładowych danych.  
  
### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a>Można wygenerować klas języka Visual Basic, które obsługuje powiązanie danych  
  
-   W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  Należy zastąpić wartość dostarczona do `/uri:` parametru o identyfikatorze URI wystąpienia usługi Northwind przykładowych danych.  
  
### <a name="to-generate-c-classes-based-on-the-service-uri"></a>Aby wygenerować klas C# opartych na identyfikator URI usługi  
  
-   W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  Należy zastąpić wartość dostarczona do `/uri:` parametru o identyfikatorze URI wystąpienia usługi Northwind przykładowych danych.  
  
### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a>Aby wygenerować klas języka Visual Basic opartych na identyfikator URI usługi  
  
-   W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  Należy zastąpić wartość dostarczona do `/uri:` parametru o identyfikatorze URI wystąpienia usługi Northwind przykładowych danych.  
  
### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a>Do generowania klasy C#, na podstawie pliku modelu koncepcyjnego (CSDL)  
  
-   W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs  
    ```  
  
### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a>Można wygenerować klas języka Visual Basic na podstawie pliku modelu koncepcyjnego (CSDL)  
  
-   W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb  
    ```  
  
### <a name="to-generate-c-classes-based-on-the-edmx-file"></a>Aby wygenerować na podstawie pliku edmx klas C#  
  
-   W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs   
    ```  
  
### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a>Aby wygenerować na podstawie pliku edmx klas języka Visual Basic  
  
-   W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb   
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie biblioteki klienta usługi danych](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 [Instrukcje: Dodawanie odwołania do usługi danych](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)  
 [Narzędzie klienta usługi danych WCF (DataSvcUtil.exe)](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)
