# 2LC3
Finals

Week 12
Theorem “Idempotency of `G`”: (G G φ)  ≡≡  (G φ)
Proof:
  Using “LTL ≡≡”:
    For any `α`, `t`:
        ⟦ (G φ) ⟧ α t
      ≡⟨ “Semantics of `G`” ⟩
        ∀ t′ : ℕ ❙ t ≤ t′ • ⟦ φ ⟧ α t′
      ≡⟨ ?, “Trading for ∀”⟩
        ∀ t′′ : ℕ • t ≤ t′′ ⇒ ⟦ φ ⟧ α t′
      ≡⟨ “Highvalue”⟩ 
        ∀ t′′ : ℕ • (∃ t′ : ℕ • t ≤ t′ ≤ t′′) ⇒ ⟦ φ ⟧ α t′′
      ≡⟨ “Witness” ⟩ 
        ∀ t′′ : ℕ • ∀ t′ : ℕ • t ≤ t′ ≤ t′′ ⇒ ⟦ φ ⟧ α t′′
      ≡⟨ “Trading for ∀” ⟩ 
        ∀ t′′ : ℕ • ∀ t′ : ℕ ❙ t ≤ t′ • t′ ≤ t′′ ⇒ ⟦ φ ⟧ α t′′
      ≡⟨ “Interchange of dummies for ∀” ⟩
        ∀ t′ : ℕ ❙ t ≤ t′ • ∀ t′′ : ℕ • t′ ≤ t′′ ⇒ ⟦ φ ⟧ α t′′
      ≡⟨“Trading for ∀” ⟩ 
        ∀ t′ : ℕ ❙ t ≤ t′ • ∀ t′′ : ℕ ❙ t′ ≤ t′′ • ⟦ φ ⟧ α t′′
      ≡⟨ “Semantics of `G`”⟩ 
        ∀ t′ : ℕ ❙ t ≤ t′ • ⟦ G φ ⟧ α t′
      ≡⟨ “Semantics of `G`” ⟩
        ⟦ (G G φ) ⟧ α t


Theorem “B via U”: (φ B ψ)  ≡≡  (¬′ ((¬′ φ) U ψ))
Proof:
  Using “LTL ≡≡”:
    For any `α`, `t`:
        ⟦ (φ B ψ) ⟧ α t
      ≡⟨ “Semantics of `B`”⟩
        ∀ t′ : ℕ ❙ t ≤ t′
              • ⟦ ψ ⟧ α t′
              ⇒ ∃ t″ : ℕ ❙ t ≤ t″ < t′ • ⟦ φ ⟧ α t″
      ≡⟨ “Trading for ∀” ⟩
        ∀ t′ : ℕ ❙ t ≤ t′
              ∧ ⟦ ψ ⟧ α t′
              • ∃ t″ : ℕ ❙ t ≤ t″ < t′ • ⟦ φ ⟧ α t″
      ≡⟨ “Generalised De Morgan” ⟩
        ¬ ∃ t′ : ℕ ❙ t ≤ t′
              ∧ ⟦ ψ ⟧ α t′
              • ∀ t″ : ℕ ❙ t ≤ t″ < t′ • ¬ ⟦ φ ⟧ α t″
      ≡⟨ “Trading for ∃”, “Semantics of LTL ¬”⟩
        ¬ ∃ t′ : ℕ ❙ t ≤ t′
              • ⟦ ψ ⟧ α t′
              ∧ ∀ t″ : ℕ ❙ t ≤ t″ < t′ • ⟦ ¬′ φ ⟧ α t″
      ≡⟨ “Semantics of `U`” ⟩
        ¬ ⟦ (¬′ φ) U ψ ⟧ α t
      ≡⟨ “Semantics of LTL ¬”⟩
        ⟦ (¬′ ((¬′ φ) U ψ)) ⟧ α t



Theorem “Negation of X”: (¬′ X φ)  ≡≡  (X ¬′ φ)
Proof:
  Using “LTL ≡≡”:
    For any `α`, `t`:
        ⟦ (¬′ X φ) ⟧ α t
      ≡⟨“Semantics of LTL ¬”⟩
        ¬ ⟦ X φ ⟧ α t
      ≡⟨“Semantics of `X`”⟩
        ¬ (⟦ φ ⟧ α) (suc t)
      ≡⟨“Semantics of LTL ¬”⟩
        ( ⟦ ¬′  φ ⟧ α) (suc t)
      ≡⟨“Semantics of `X`”⟩
        ⟦ (X ¬′ φ) ⟧ α t



Theorem “V via B”: (φ V ψ)  ≡≡  (φ B ¬′ ψ)
Proof:
  Using “LTL ≡≡”:
    For any α, t:
        ⟦ (φ V ψ) ⟧ α t
      ≡⟨“Semantics of V”⟩
        (∀ t′ : ℕ ❙ t ≤ t′ ∧ ¬ ⟦ ψ ⟧ α t′ • ∃ t″ ❙ t ≤ t″ < t′ • ⟦ φ ⟧ α t″)
      ≡⟨“Trading for ∀”⟩
        (∀ t′ : ℕ ❙ t ≤ t′ • ¬ (⟦ ψ ⟧ α) t′ ⇒ (∃ t″ : ℕ ❙ t ≤ t″ < t′ • (⟦ φ ⟧ α) t″ ) )   
      ≡⟨“Semantics of LTL ¬”⟩
        (∀ t′ : ℕ ❙ t ≤ t′ • (⟦ (¬′ ψ) ⟧ α) t′ ⇒ (∃ t″ : ℕ ❙ t ≤ t″ < t′ • (⟦ φ ⟧ α) t″ ) )   
      ≡⟨“Semantics of B”⟩
        ⟦ (φ B ¬′ ψ) ⟧ α t


╍╍╍ Axiom “Semantics of B”: (⟦ (φ B ψ) ⟧ α) t ≡ (∀ t′ : ℕ ❙ t ≤ t′ • (⟦ ψ ⟧ α) t′ ⇒ (∃ t″ : ℕ ❙ t ≤ t″ < t′ • (⟦ φ ⟧ α) t″ ) )   
╍╍╍ Axiom “Semantics of LTL ¬”: (⟦ (¬′ φ) ⟧ α) t ≡ ¬ (⟦ φ ⟧ α) t


Lemma “Semantics of Y”:
    ⟦ Y φ ⟧ α t ≡ t ≠ 0 ∧ ⟦ φ ⟧ α (pred t)
Proof:
  By induction on t : ℕ:
    Base case:
        ⟦ Y φ ⟧ α 0 
      ≡⟨“Semantics of Y”⟩
        false
      ≡⟨“Irreflexivity of ≠”, “Zero of ∧”⟩
        0 ≠ 0 ∧ ⟦ φ ⟧ α (pred 0)
    Induction step:
        ⟦ Y φ ⟧ α (suc t)
      ≡⟨“Semantics of Y”⟩
        ⟦ φ ⟧ α t
      ≡⟨“Identity of ∧”⟩
        true ∧ ⟦ φ ⟧ α t
      ≡⟨“Zero is not successor”⟩
        (suc t) ≠ 0 ∧ ⟦ φ ⟧ α t
      ≡⟨“Predecessor of successor”⟩
        suc t ≠ 0 ∧ ⟦ φ ⟧ α (pred (suc t))


Lemma “Semantics of Z”:
    ⟦ Z φ ⟧ α t  ≡  t = 0 ∨ ⟦ φ ⟧ α (pred t)
Proof:
  By induction on t : ℕ:
    Base case:
        ⟦ Z φ ⟧ α 0 
      ≡⟨“Semantics of Z”⟩ 
        true
      ≡⟨“Zero of ∨”, “Reflexivity of =”⟩
        0 = 0 ∨ ⟦ φ ⟧ α (pred 0)
    Induction step:
        ⟦ Z φ ⟧ α (suc t)
      ≡⟨“Semantics of Z”⟩
        ⟦ φ ⟧ α t
      ≡⟨“Identity of ∨”⟩
        false ∨ ⟦ φ ⟧ α t
      ≡⟨“Zero is not successor”⟩
        (suc t) = 0 ∨ ⟦ φ ⟧ α t
      ≡⟨“Predecessor of successor”⟩
        (suc t) = 0 ∨ ⟦ φ ⟧ α (pred (suc t))


Theorem “Reflexivity of LTL ≡≡”: φ ≡≡ φ
Proof:
    φ ≡≡ φ 
  ≡⟨“LTL ≡≡”⟩
    (∀ α : A → ℕ → 𝔹 • ∀ t : ℕ • ⟦ φ ⟧ α t ≡ ⟦ φ ⟧ α t)
  ≡⟨“Reflexivity of ≡”⟩ 
    (∀ α : A → ℕ → 𝔹 • ∀ t : ℕ • true)
  ≡⟨“True ∀ body”⟩
    true


Theorem “Symmetry of LTL ≡≡”: φ ≡≡ ψ  ≡  ψ ≡≡ φ
Proof:
    φ ≡≡ ψ
  ≡⟨“LTL ≡≡”⟩
    ∀ α : A → ℕ → 𝔹 • ∀ t : ℕ • ⟦ φ ⟧ α t ≡ ⟦ ψ ⟧ α t
  ≡⟨“Symmetry of ≡”⟩
    ∀ α : A → ℕ → 𝔹 • ∀ t : ℕ • ⟦ ψ ⟧ α t ≡ ⟦ φ ⟧ α t 
  ≡⟨“LTL ≡≡”⟩
    ψ ≡≡ φ


Theorem “Transitivity of LTL ≡≡”: φ ≡≡ χ ≡≡ ψ  ⇒  φ ≡≡ ψ
Proof:
  Assuming φ ≡≡ χ ∧ χ ≡≡ ψ and using with “LTL ≡≡”: 
    Using “LTL ≡≡”:
      For any α, t:
          ⟦ φ ⟧ α t
        ≡⟨ Assumption φ ≡≡ χ ∧ χ ≡≡ ψ⟩
          ⟦ χ ⟧ α t
        ≡⟨ Assumption φ ≡≡ χ ∧ χ ≡≡ ψ⟩
          ⟦ ψ ⟧ α t

Lemma “Symmetry of LTL ∧”:  (φ ∧′ ψ) ≡≡ (ψ ∧′ φ)
Proof:
  Using “LTL ≡≡”:
    For any α, t:
        ⟦ φ ∧′ ψ ⟧ α t ≡ ⟦ ψ ∧′ φ ⟧ α t
      ≡⟨“Semantics of LTL ∧”, “Symmetry of ∧”, “Reflexivity of ≡”⟩
        true


Lemma “Symmetry of LTL ∨”:  (φ ∨′ ψ) ≡≡ (ψ ∨′ φ)
Proof:
  Using “LTL ≡≡”:
    For any α, t:
        ⟦ φ ∨′ ψ ⟧ α t ≡ ⟦ ψ ∨′ φ ⟧ α t
      ≡⟨“Semantics of LTL ∨”, “Symmetry of ∨”, “Reflexivity of ≡”⟩
        true


Lemma “Symmetry of LTL ⇔”:  (φ ⇔′ ψ) ≡≡ (ψ ⇔′ φ)
Proof:
  Using “LTL ≡≡”:
    For any α, t:
        ⟦ φ ⇔′ ψ ⟧ α t ≡ ⟦ ψ ⇔′ φ ⟧ α t
      ≡⟨“Semantics of LTL ⇔”, “Reflexivity of ≡”⟩
        true

Lemma “Associativity of LTL ∧”:
  ((φ ∧′ ψ) ∧′ χ) ≡≡ (φ ∧′ (ψ ∧′ χ))
Proof:
  Using “LTL ≡≡”:
    For any α, t:
        ⟦ ((φ ∧′ ψ) ∧′ χ) ⟧ α t
      ≡⟨“Semantics of LTL ∧”⟩
        ⟦ (φ ∧′ ψ) ⟧ α t ∧ ⟦ χ ⟧ α t
      ≡⟨“Semantics of LTL ∧”⟩
        ⟦ φ ⟧ α t ∧ ⟦ ψ ⟧ α t ∧ ⟦ χ ⟧ α t
      ≡⟨ “Symmetry of ∧”⟩
        ⟦ φ ⟧ α t ∧ ( ⟦ ψ ⟧ α t ∧ ⟦ χ ⟧ α t )
      ≡⟨ “Semantics of LTL ∧”⟩
        ⟦ φ ⟧ α t ∧ ⟦ (ψ ∧′ χ) ⟧ α t
      ≡⟨ “Semantics of LTL ∧”⟩
        ⟦ (φ ∧′ (ψ ∧′ χ)) ⟧ α t


Lemma “Absorption of LTL ∨ by ∧”:
  (φ ∧′ (φ ∨′ ψ)) ≡≡ φ
Proof:
  Using “LTL ≡≡”:
    For any α, t:
        ⟦ (φ ∧′ (φ ∨′ ψ)) ⟧ α t
      ≡⟨“Semantics of LTL ∧”⟩
        ⟦ φ ⟧ α t ∧ ⟦ (φ ∨′ ψ) ⟧ α t
      ≡⟨“Semantics of LTL ∨”⟩
        ⟦ φ ⟧ α t ∧ (⟦ φ ⟧ α t ∨ ⟦ ψ ⟧ α t)
      ≡⟨“Absorption”⟩
        ⟦ φ ⟧ α t


Theorem “Negation of X”: (¬′ X φ)  ≡≡  (X ¬′ φ)
Proof:  
  Using “LTL ≡≡”:
    For any α, t:
        ⟦ (¬′ X φ) ⟧ α t
      ≡⟨“Semantics of LTL ¬”⟩
        ¬ ⟦ X φ ⟧ α t
      ≡⟨“Semantics of X”⟩
        ¬ (⟦ φ ⟧ α) (suc t)
      ≡⟨“Semantics of LTL ¬”⟩
        ( ⟦ ¬′  φ ⟧ α) (suc t)
      ≡⟨“Semantics of X”⟩
        ⟦ (X ¬′ φ) ⟧ α t
        

╍╍╍ Axiom “Semantics of X”: (⟦ (X φ) ⟧ α) t ≡ (⟦ φ ⟧ α) (suc t)
╍╍╍ Axiom “Semantics of LTL ¬”: ⟦ ¬′ φ ⟧ α t ≡ ¬ ⟦ φ ⟧ α t


Theorem “G via F”: (G φ)  ≡≡  (¬′ F ¬′ φ)
Proof:
  Using “LTL ≡≡”: 
    For any α, t:
        ⟦ (G φ) ⟧ α t
      ≡⟨“Semantics of G”⟩
        (∀ t′ : ℕ ❙ t ≤ t′ • (⟦ φ ⟧ α) t′ )
      ≡⟨“Generalised De Morgan”⟩
        ¬ (∃ t′ : ℕ ❙ t ≤ t′ • ¬ (⟦ φ ⟧ α) t′ )
      ≡⟨“Semantics of LTL ¬”⟩  
        ¬ (∃ t′ : ℕ ❙ t ≤ t′ • (⟦ ¬′ φ ⟧ α) t′ )
      ≡⟨“Semantics of F”⟩
        ¬ ⟦ (F ¬′ φ) ⟧ α t
      ≡⟨“Semantics of LTL ¬”⟩
        ⟦ (¬′ F ¬′ φ) ⟧ α t


Theorem “V via B”: (φ V ψ)  ≡≡  (φ B ¬′ ψ)
Proof:
  Using “LTL ≡≡”:
    For any α, t:
        ⟦ (φ V ψ) ⟧ α t
      ≡⟨“Semantics of V”⟩
        (∀ t′ : ℕ ❙ t ≤ t′ ∧ ¬ ⟦ ψ ⟧ α t′ • ∃ t″ ❙ t ≤ t″ < t′ • ⟦ φ ⟧ α t″)
      ≡⟨“Trading for ∀”⟩
        (∀ t′ : ℕ ❙ t ≤ t′ • ¬ (⟦ ψ ⟧ α) t′ ⇒ (∃ t″ : ℕ ❙ t ≤ t″ < t′ • (⟦ φ ⟧ α) t″ ) )   
      ≡⟨“Semantics of LTL ¬”⟩
        (∀ t′ : ℕ ❙ t ≤ t′ • (⟦ (¬′ ψ) ⟧ α) t′ ⇒ (∃ t″ : ℕ ❙ t ≤ t″ < t′ • (⟦ φ ⟧ α) t″ ) )   
      ≡⟨“Semantics of B”⟩
        ⟦ (φ B ¬′ ψ) ⟧ α t

Theorem “G via V”: (G φ)  ≡≡  (FALSE V φ)
Proof:
  Using “LTL ≡≡”:
    For any α, t:
        ⟦ (G φ) ⟧ α t
      =⟨“Semantics of G”⟩
        (∀ t′ : ℕ ❙ t ≤ t′ • (⟦ φ ⟧ α) t′ )
      =⟨“Identity of ∨”⟩
        false ∨ (∀ t′ : ℕ ❙ t ≤ t′ • (⟦ φ ⟧ α) t′ )
      =⟨ “Double negation”, “Negation of false”⟩
        ¬ ( true )
        ∨ (∀ t′ : ℕ ❙ t ≤ t′ • (⟦ φ ⟧ α) t′ )
      =⟨“True ∀ body”⟩ 
        ¬ (∀ t″ : ℕ ❙ t ≤ t″ • ( true ) )
        ∨ (∀ t′ : ℕ ❙ t ≤ t′ • (⟦ φ ⟧ α) t′ )
      =⟨“Zero of ∨”⟩
        ¬ (∀ t″ : ℕ ❙ t ≤ t″ • ( true ∨ ¬(∀ t′ : ℕ ❙ t ≤ t′ ≤ t″ • (⟦ φ ⟧ α) t′ ) ) )
        ∨ (∀ t′ : ℕ ❙ t ≤ t′ • (⟦ φ ⟧ α) t′ )
      =⟨“Negation of false”⟩
        ¬ (∀ t″ : ℕ ❙ t ≤ t″ • (¬ false ∨ ¬(∀ t′ : ℕ ❙ t ≤ t′ ≤ t″ • (⟦ φ ⟧ α) t′ ) ) )
        ∨ (∀ t′ : ℕ ❙ t ≤ t′ • (⟦ φ ⟧ α) t′ )
      =⟨“De Morgan”⟩
        ¬ (∀ t″ : ℕ ❙ t ≤ t″ • ¬ (false ∧ (∀ t′ : ℕ ❙ t ≤ t′ ≤ t″ • (⟦ φ ⟧ α) t′ ) ) )
        ∨ (∀ t′ : ℕ ❙ t ≤ t′ • (⟦ φ ⟧ α) t′ )
      =⟨“Identity of ∧”⟩
        ¬ (∀ t″ : ℕ ❙ t ≤ t″ • ¬ (false ∧ (∀ t′ : ℕ ❙ t ≤ t′ ≤ t″ • (⟦ φ ⟧ α) t′ ) ) )
        ∨ (∀ t′ : ℕ ❙ t ≤ t′ • true ∧ (⟦ φ ⟧ α) t′ )
      =⟨“Generalised De Morgan”⟩
        ¬ (∀ t″ : ℕ ❙ t ≤ t″ • ¬ (false ∧ (∀ t′ : ℕ ❙ t ≤ t′ ≤ t″ • (⟦ φ ⟧ α) t′ ) ) )
        ∨ ¬ (∃ t′ : ℕ ❙ t ≤ t′ • ¬ (true ∧ (⟦ φ ⟧ α) t′) )
      =⟨“Generalised De Morgan”⟩
        (∃ t″ : ℕ ❙ t ≤ t″ • false ∧ 
        (∀ t′ : ℕ ❙ t ≤ t′ ≤ t″ • (⟦ φ ⟧ α) t′ ) ) 
        ∨ (∀ t′ : ℕ ❙ t ≤ t′ • true
        ∧ (⟦ φ ⟧ α) t′ )
      =⟨“Negation of false”⟩
        (∃ t″ : ℕ ❙ t ≤ t″ • false ∧ 
        (∀ t′ : ℕ ❙ t ≤ t′ ≤ t″ • (⟦ φ ⟧ α) t′ ) ) 
        ∨ (∀ t′ : ℕ ❙ t ≤ t′ • ¬ false
        ∧ (⟦ φ ⟧ α) t′ )
      =⟨“Semantics of FALSE”⟩
        (∃ t″ : ℕ ❙ t ≤ t″ • (⟦ FALSE ⟧ α) t″ ∧ 
        (∀ t′ : ℕ ❙ t ≤ t′ ≤ t″ • (⟦ φ ⟧ α) t′ ) ) 
        ∨ (∀ t′ : ℕ ❙ t ≤ t′ • ¬ (⟦ FALSE ⟧ α) t′ 
        ∧ (⟦ φ ⟧ α) t′ )   
      =⟨“Semantics of V”⟩
        ⟦ FALSE V φ ⟧ α t
   






