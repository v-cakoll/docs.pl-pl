---
title: 'Instrukcje: Ręczne Generowanie klas usługi danych klienta (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: fbf3a3a2ee52df95780f715e1358a042eb7dd02c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128664"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a>Instrukcje: Ręczne Generowanie klas usługi danych klienta (WCF Data Services)
Usługi danych WCF integruje się z programem Visual Studio, aby umożliwić automatyczne generowanie klas usługi danych klienta, gdy używasz **Dodaj odwołanie do usługi** okno dialogowe, aby dodać odwołanie do usługi danych w projekcie programu Visual Studio. Aby uzyskać więcej informacji, zobacz [jak: Dodaj odwołanie do usługi danych](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md). Możesz również ręcznie wygenerować tych samych klas usługi danych klienta przy użyciu narzędzia do generowania kodu `DataSvcUtil.exe`. To narzędzie, który jest dołączony do usługi danych WCF, generuje klas .NET Framework na podstawie definicji usługi danych. Może również służyć do Generowanie klas usługi danych z pliku modelu koncepcyjnego (.csdl), a także z pliku edmx, który reprezentuje model Entity Framework w projekcie programu Visual Studio.

 Ten przykład, w tym temacie tworzy klas usługi danych klienta oparte na usługę Northwind przykładowych danych. Ta usługa zostanie utworzona po zakończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Przykłady w tym temacie wymagają pliku modelu koncepcyjnego dla modelu Northwind. Aby uzyskać więcej informacji, zobacz [jak: Generowanie modelu i mapowania plików za pomocą EdmGen.exe](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md). Przykłady w tym temacie wymagają pliku edmx dla modelu Northwind. Aby uzyskać więcej informacji, zobacz [Omówienie pliku edmx](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4).

### <a name="to-generate-c-classes-that-support-data-binding"></a>Można wygenerować klas języka C#, które obsługuje powiązanie danych

-   W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  Należy zastąpić wartość dostarczona do `/uri:` parametru za pomocą identyfikatora URI wystąpienia usługi Northwind przykładowych danych.

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a>Do generowania klasy Visual Basic, które obsługuje powiązanie danych

-   W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  Należy zastąpić wartość dostarczona do `/uri:` parametru za pomocą identyfikatora URI wystąpienia usługi Northwind przykładowych danych.

### <a name="to-generate-c-classes-based-on-the-service-uri"></a>Można wygenerować klas języka C# oparte na identyfikator URI usługi

-   W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  Należy zastąpić wartość dostarczona do `/uri:` parametru za pomocą identyfikatora URI wystąpienia usługi Northwind przykładowych danych.

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a>Do generowania klasy Visual Basic, w oparciu o identyfikator URI usługi

-   W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  Należy zastąpić wartość dostarczona do `/uri:` parametru za pomocą identyfikatora URI wystąpienia usługi Northwind przykładowych danych.

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a>Można wygenerować klas języka C# na podstawie pliku modelu koncepcyjnego (CSDL)

-   W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a>Do generowania klasy Visual Basic na podstawie pliku modelu koncepcyjnego (CSDL)

-   W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a>Można wygenerować klas języka C# na podstawie pliku edmx

-   W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a>Do generowania klasy Visual Basic na podstawie pliku edmx

-   W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a>Zobacz też

- [Generowanie biblioteki klienta usługi danych](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)
- [Jak: Dodaj odwołanie do usługi danych](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
- [Narzędzie klienta usługi danych WCF (DataSvcUtil.exe)](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)