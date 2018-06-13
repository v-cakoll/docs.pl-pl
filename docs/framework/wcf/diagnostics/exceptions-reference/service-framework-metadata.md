---
title: Metadane struktury usługi
ms.date: 03/30/2017
ms.assetid: 76afc73a-0770-4084-93f3-6701a757911e
ms.openlocfilehash: f65f53ff99202275876fb6e3c431bc49ae2bd38b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474353"
---
# <a name="service-framework-metadata"></a>Metadane struktury usługi
W tym temacie wymieniono wszystkie wyjątki generowane przez metadane struktury usługi.  
  
## <a name="exception-list"></a>Listy wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|AsyncEndCalledOnWrongChannel|Asynchroniczne End została wywołana dla niewłaściwego kanału.|  
|AsyncEndCalledWithAnIAsyncResult|Asynchroniczne End została wywołana z użyciem argumentu IAsyncResult z innej metody Begin.|  
|AttemptedToGetContractTypeForButThatTypeIs1|Próbowano uzyskać typ kontraktu dla określonego. Typ nie jest elementem ServiceContract i dziedziczy go.|  
|CannotHaveTwoOperationsWithTheSameName3|Nie może zawierać dwóch operacji w tym samym kontrakcie o takiej samej nazwie. Metody określonej w określonym typie naruszają tę regułę. Zmień nazwę jednej z operacji, zmieniając nazwę metody lub używając właściwości Name elementu OperationContractAttribute.|  
|CannotInheritTwoOperationsWithTheSameName3|Nie można dziedziczyć dwóch różnych operacji o tej samej nazwie. Określona operacja z określonym umów naruszają tę regułę. Zmień nazwę jednej z operacji, zmieniając nazwę metody lub używając właściwości Name elementu OperationContractAttribute.|  
|CantCreateChannelWithManualAddressing|Nie można utworzyć kanału dla kontraktu wymagającego żądań i odpowiedzi oraz powiązania wymagającego ręcznego adresowania, ale tylko obsługującego komunikację dupleksową.|  
|DuplicateBehavior1|Nie można dodać wartości do kolekcji. Kolekcja zawiera już element tego samego określonego typu. Ta kolekcja obsługuje tylko jedno wystąpienie każdego typu.|  
|InAContractInheritanceHierarchyIfParentHasCallbackChildMustToo|Kontraktu określonej usługi podstawowej ma kontrakt wywołania zwrotnego określony, kontrakt określoną usługę pochodnego również musi określać określonego typu lub typu pochodnego jako jej kontrakt wywołania zwrotnego.|  
|InvalidAsyncBeginMethodSignatureForMethod2|Nieprawidłowy asynchronicznego Begin podpis metody dla określonej metody w określonym typie ServiceContract. Twoje rozpocząć metody musi przyjmować element AsyncCallback oraz dowolny obiekt jako dwa ostatnie argumenty i zwracać obiekt IAsyncResult.|  
|InvalidAsyncEndMethodSignatureForMethod2|Nieprawidłowy asynchroniczne zakończenia podpis metody dla określonej metody w określonym typie ServiceContract. Stosowana metoda end musi przyjmować obiekt IAsyncResult jako ostatni argument.|  
|MessagePropertiesArraySize0|Tablica, która została przekazana nie ma wystarczającej ilości miejsca dla wszystkich właściwości zawarte w tej kolekcji.|  
|OneWayAndFaultsIncompatible2|Określona metoda w typie określonym jest oznaczona jako IsOneWay = true, ale deklaruje co najmniej jeden element Faultcontractattribute. Metody jednokierunkowe nie mogą deklarować elementów Faultcontractattribute. Zmień ustawienie właściwości IsOneWay na false lub usuń elementy Faultcontractattribute.|  
|UnsupportedWSDLOnlyOneMessage|Nieobsługiwany Web Services Description Language. Komunikaty o błędach jest obsługiwana tylko jednej części wiadomości. Ten komunikat o błędzie odwołuje się do więcej niż jedną część komunikatu. Jeśli istnieje możliwość edytowania pliku Web Services Description Language, można naprawić problem, usuwając zbędne części wiadomości w taki, który fault tylko do jednej części odwołuje się do komunikatu.|  
|UnsupportedWSDLTheFault|Nieobsługiwany Web Services Description Language. Błąd części komunikatu musi odwoływać się do elementu. Ten komunikat o błędzie nie odwołuje się do elementu. Jeśli masz dostęp do edycji w dokumencie języka definicji usługi sieci Web, należy rozwiązać problem, umieszczając odwołanie do elementu schematu za pomocą atrybutu "element".|  
|WsdlImportErrorDependencyDetail|Wystąpił błąd podczas importowania określonego czy określona wartość jest zależna od. Wyrażenie Xpath jest określona.|  
|XsdMissingRequiredAttribute1|Brak określonego wymaganego atrybutu.|
