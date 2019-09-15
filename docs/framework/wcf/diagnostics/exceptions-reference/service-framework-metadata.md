---
title: Metadane struktury usługi
ms.date: 03/30/2017
ms.assetid: 76afc73a-0770-4084-93f3-6701a757911e
ms.openlocfilehash: f3e73df54b3389b2c9f27001953be147b27eb6f8
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991202"
---
# <a name="service-framework-metadata"></a>Metadane struktury usługi
W tym temacie wymieniono wszystkie wyjątki wygenerowane przez metadane struktury usług.  
  
## <a name="exception-list"></a>Lista wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|AsyncEndCalledOnWrongChannel|Asynchroniczne zakończenie zostało wywołane dla niewłaściwego kanału.|  
|AsyncEndCalledWithAnIAsyncResult|Asynchroniczne zakończenie zostało wywołane z elementem IAsyncResult z innej metody BEGIN.|  
|AttemptedToGetContractTypeForButThatTypeIs1|Podjęto próbę pobrania typu kontraktu dla określonego elementu. Typ nie jest kontraktem ServiceContract i nie dziedziczy kontraktu ServiceContract.|  
|CannotHaveTwoOperationsWithTheSameName3|Nie mogą istnieć dwie operacje w tym samym kontrakcie o tej samej nazwie. Określone metody w określonym typie naruszają tę regułę. Zmień nazwę jednej z operacji, zmieniając nazwę metody lub używając właściwości Name obiektu OperationContractAttribute.|  
|CannotInheritTwoOperationsWithTheSameName3|Nie można dziedziczyć dwóch różnych operacji o tej samej nazwie. Określona operacja z określonych kontraktów narusza tę regułę. Zmień nazwę jednej z operacji, zmieniając nazwę metody lub używając właściwości Name obiektu OperationContractAttribute.|  
|CantCreateChannelWithManualAddressing|Nie można utworzyć kanału dla kontraktu wymagającego żądania/odpowiedzi oraz powiązania wymagającego ręcznego adresowania, ale tylko obsługują komunikację dupleksową.|  
|DuplicateBehavior1|Nie można dodać wartości do kolekcji. Kolekcja zawiera już element tego samego określonego typu. Ta kolekcja obsługuje tylko jedno wystąpienie każdego typu.|  
|InAContractInheritanceHierarchyIfParentHasCallbackChildMustToo|Ponieważ określony kontrakt usługi podstawowej ma określony kontrakt wywołania zwrotnego, określony kontrakt usługi pochodnej musi również określać określony typ lub typ pochodny jako kontrakt wywołania zwrotnego.|  
|InvalidAsyncBeginMethodSignatureForMethod2|Nieprawidłowa sygnatura asynchronicznej metody BEGIN dla określonej metody w określonym typie ServiceContract. Metoda BEGIN musi przyjmować element AsyncCallback i Object jako ostatnie dwa argumenty i zwracać element IAsyncResult.|  
|InvalidAsyncEndMethodSignatureForMethod2|Nieprawidłowa sygnatura asynchronicznej metody end dla określonej metody w określonym typie ServiceContract. Metoda End musi przyjmować element IAsyncResult jako ostatni argument.|  
|MessagePropertiesArraySize0|Przekazano tablicę, która nie ma wystarczającej ilości miejsca, aby pomieścić wszystkie właściwości zawarte w tej kolekcji.|  
|OneWayAndFaultsIncompatible2|Określona metoda w określonym typie jest oznaczona jako IsOneWay = true i deklaruje co najmniej jedną element FaultContractAttributes. Metody jednokierunkowe nie mogą deklarować element FaultContractAttributes. Zmień wartość IsOneWay na false lub Usuń element FaultContractAttributes.|  
|UnsupportedWSDLOnlyOneMessage|Nieobsługiwana Web Services Description Language. Dla komunikatów o błędach jest obsługiwana tylko jedna część komunikatów. Ten komunikat o błędzie odnosi się do więcej niż jednej części wiadomości. Jeśli masz uprawnienia do edycji pliku Web Services Description Language, możesz rozwiązać ten problem, usuwając dodatkowe części komunikatów, takie jak komunikaty o błędach, które odwołują się tylko do jednej części.|  
|UnsupportedWSDLTheFault|Nieobsługiwana Web Services Description Language. Część komunikatu o błędzie musi odwoływać się do elementu. Ten komunikat o błędzie nie odwołuje się do elementu. Jeśli masz uprawnienia do edycji dokumentu języka definicji usług sieci Web, możesz rozwiązać ten problem, odwołując się do elementu schematu przy użyciu atrybutu "element".|  
|WsdlImportErrorDependencyDetail|Wystąpił błąd podczas importowania określonego, czy inna określona wartość jest zależna od. Określono również wyrażenie XPath.|  
|XsdMissingRequiredAttribute1|Brak określonego wymaganego atrybutu.|
