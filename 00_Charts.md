# Charts and diagrams

Charts and diagrams used in the dissertation are created using [Mermaid](https://mermaid-js.github.io/mermaid/#/).

## Challenges

### Mind map of selected challenges driven by EV adoption

```mermaid
mindmap
  root(("Challenges driven by adoption of EVs"))
  ::icon(fa fa-car)
    Recycling
    ::icon(fa fa-recycle)
        Battery
    EV charging
    ::icon(fa fa-plug)
        Battery technology
            Raw materials
        Charging infrastructure        
            Impact on the Grid
            [Change in driver behaviour]
        Policies and commercials
    Car design and manufacture
    ::icon(fa fa-industry)
        Drivetrain and propulsion
        Design for EV    
    Norms and standards
    ::icon(fa fa-balance-scale)
        Regulations
        Taxing
        Incentives
```

## Analytic framework

### Simple version of the analytic framework

```mermaid
flowchart LR
  DAT1[(fa:fa-table Charging</br>dataset)]
  DAT2[(fa:fa-map-marked-alt Spatial<br/>datasets<br>)]
  DAT3[fa:fa-server Data<br>engineering]
  CLU1(fa:fa-spinner Clustering)
  CLA1(fa:fa-spinner Classification)
  RES1[[fa:fa-chart-bar Results]]

  DAT1 --> DAT3
  DAT2 --> DAT3
  DAT3 --> CLU1
  subgraph Modelling
    CLU1 -- "fa:fa-check-double Validation" --> CLU1
    CLU1 --> CLA1
    CLA1 -- "fa:fa-check-double Validation" --> CLA1
  end
  CLA1 --> RES1
```

### A more detailed version of the analytic framework

```mermaid
flowchart LR
    A[(fa:fa-table Charging<br>Session</br>dataset)] --> C("`fa:fa-code Feature extraction 
            *(ground truth)*`")
    AA[(fa:fa-map-marked-alt Spatial<br/>datasets<br>)] --> C
    A --> CLN(fa:fa-bath Cleaning)
    subgraph Data engineering
    C --> CLN(fa:fa-bath Cleaning) --> B(fa:fa-filter Feature selection)
    end
    subgraph Modelling
        B --> SCAL1(fa:fa-ruler Scaling)
        B --> SCAL2(fa:fa-ruler Scaling)
        CLU2 --> CLA1
        SCAL1 --> CLU1(fa:fa-spinner Clustering)
        SCAL2 --> CLA1(fa:fa-spinner Classification)
        subgraph Clustering
        CLU1 --> CLU2[fa:fa-project-diagram Clusters]
        CLU2 --> CLU3(fa:fa-check-double Validation)
        CLU2 -..-> CLU5(fa:fa-book-reader Interpretation)
        CLU3 --> CLU1

        end
        subgraph Classification
        CLA3 --> CLA4(fa:fa-check-double Validation)
        CLA1 --> CLA3[fa:fa-project-diagram Classes]
        CLA4 --> CLA1
        CLA3 --> CLA2[fa:fa-book-reader Interpretation]
        end
    end
    CLU5(fa:fa-book-reader Interpretation) -..-> K
    CLA2 --> K[[fa:fa-book Knowledge]]
```
