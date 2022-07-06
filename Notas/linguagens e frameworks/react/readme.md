# React


## Performance

### memo

1. Pure Function Component
2. Re-render muitas vezes
3. Re-renders com as mesma propriedades
4. Componentes grandes

### useMemo

1. Evitar re-calculo de propriedades
2. Shallow compare

### useCallback

1. Resolver problemas de igualdade referencial (recriar funções quando estado mudar)
2. Funções complexas
3. Deep compare