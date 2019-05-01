---
title: Metadane struktury usługi
ms.date: 03/30/2017
ms.assetid: 76afc73a-0770-4084-93f3-6701a757911e
ms.openlocfilehash: f65f53ff99202275876fb6e3c431bc49ae2bd38b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780802"
---
# <a name="service-framework-metadata"></a>Metadane struktury usługi
Ten temat zawiera listę wszystkich wyjątków generowanych przez metadane struktury usługi.  
  
## <a name="exception-list"></a>Lista wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|AsyncEndCalledOnWrongChannel|Końca asynchronicznego została wywołana dla niewłaściwego kanału.|  
|AsyncEndCalledWithAnIAsyncResult|Końca asynchronicznego została wywołana z elementem IAsyncResult z innej metody Begin.|  
|AttemptedToGetContractTypeForButThatTypeIs1|Próbowano uzyskać typ kontraktu dla określonego. Typ nie jest typu ServiceContract i dziedziczy go.|  
|CannotHaveTwoOperationsWithTheSameName3|Nie może mieć dwie operacje w tej samej umowy o takiej samej nazwie. Określonej metody w określonym typie narusza tę regułę. Zmień nazwę jednej z operacji, zmieniając nazwę metody lub używając właściwości Name obiektu OperationContractAttribute.|  
|CannotInheritTwoOperationsWithTheSameName3|Nie można dziedziczyć dwóch różnych operacji o tej samej nazwie. Określona operacja z określonym umów narusza tę regułę. Zmień nazwę jednej z operacji, zmieniając nazwę metody lub używając właściwości Name obiektu OperationContractAttribute.|  
|CantCreateChannelWithManualAddressing|Nie można utworzyć kanału dla kontraktu wymagającego żądań i odpowiedzi oraz powiązania wymagającego ręcznego adresowania, ale tylko obsługującego komunikację dupleksową.|  
|DuplicateBehavior1|Nie można dodać wartości do kolekcji. Kolekcja zawiera już element tego samego określonego typu. Ta kolekcja obsługuje tylko jedno wystąpienie każdego typu.|  
|InAContractInheritanceHierarchyIfParentHasCallbackChildMustToo|Kontrakt określony usługi podstawowej ma kontrakt określonego wywołania zwrotnego, kontrakt określony pochodnej usługi należy także określić określonego typu lub typem pochodnym jako jej kontrakt wywołania zwrotnego.|  
|InvalidAsyncBeginMethodSignatureForMethod2|Nieprawidłowy asynchronicznego Begin podpis metody dla określonej metody w określonym typie ServiceContract. Twoje rozpocząć metody musi przyjmować element AsyncCallback oraz dowolny obiekt jako dwa ostatnie argumenty i zwracać obiekt IAsyncResult.|  
|InvalidAsyncEndMethodSignatureForMethod2|Nieprawidłowy asynchronicznego zakończenia podpis metody dla określonej metody w określonym typie ServiceContract. Metoda end musi przyjmować obiekt IAsyncResult jako ostatni argument.|  
|MessagePropertiesArraySize0|Tablica, która została przekazana nie ma wystarczającej ilości miejsca do przechowywania wszystkich właściwości, które są zawarte w tej kolekcji.|  
|OneWayAndFaultsIncompatible2|Określonej metodzie w określonym typie jest oznaczona jako IsOneWay = true, ale deklaruje co najmniej jeden element FaultContractAttributes. Metody jednokierunkowe nie mogą deklarować elementów FaultContractAttributes. Zmień ustawienie właściwości IsOneWay na wartość false lub Usuń element FaultContractAttributes.|  
|UnsupportedWSDLOnlyOneMessage|Nieobsługiwana Web Services Description Language. Komunikaty o błędach jest obsługiwana tylko jednej części wiadomości. Ten komunikat o błędzie odnosi się do więcej niż jedną część komunikatu. Jeśli masz dostęp do edycji pliku Web Services Description Language można rozwiązanie problemu, usuwając zbędne części wiadomości w taki, który błędów komunikat odwołania tylko jeden element.|  
|UnsupportedWSDLTheFault|Nieobsługiwana Web Services Description Language. Część wiadomości błędu musi odwoływać się do elementu. Ten komunikat o błędzie nie odwołuje się do elementu. Jeśli masz dostęp do edycji w dokumencie języka definicji usługi sieci Web, możesz rozwiązać problem, odwołując się do elementu schematu za pomocą atrybutu "element".|  
|WsdlImportErrorDependencyDetail|Wystąpił błąd podczas importowania określonego to zależy od określonej wartości. Wyrażenie Xpath jest także określona.|  
|XsdMissingRequiredAttribute1|Brak określonego wymaganego atrybutu.|
